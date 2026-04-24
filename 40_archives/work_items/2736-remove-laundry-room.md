---
title: 2736-remove-laundry-room
type: work-item
item_type: task
project: houseplans.net
status: ready
created: 2026-04-23
updated:
due:
assignee:
url: https://trello.com/c/fNSsIZqV/2736-remove-laundry-room
---

# 2736-remove-laundry-room

## Description

The following tours need the laundry room removed:

009-00326  
009-00338  
009-00331  
009-00343  
009-00320  
009-00334  
009-00354  
009-00350  
009-00344  
009-00319  
009-00311  
009-00314  
009-00353  
009-00345  
009-00363  
009-00323  
009-00328  
009-00325  
009-00347  
009-00324  
009-00332  
009-00313  
009-00349

---

PHP shell script to run in the tours directory, with a dry-run, change $write to true to run.

```
php <<'PHP'
<?php

declare(strict_types=1);

$write = false; // change to true for actual run

$toursDir = __DIR__;

$plans = [
    '009-00326',
    '009-00338',
    '009-00331',
    '009-00343',
    '009-00320',
    '009-00334',
    '009-00354',
    '009-00350',
    '009-00344',
    '009-00319',
    '009-00311',
    '009-00314',
    '009-00353',
    '009-00345',
    '009-00363',
    '009-00323',
    '009-00328',
    '009-00325',
    '009-00347',
    '009-00324',
    '009-00332',
    '009-00313',
    '009-00349',
];

foreach ($plans as $plan) {
    $file = $toursDir . '/' . $plan . '/app-files/data.js';

    if (!is_file($file)) {
        echo "[skip] {$plan}: missing {$file}\n";
        continue;
    }

    $contents = file_get_contents($file);
    if (!preg_match('/^var APP_DATA = (.*);\s*$/s', $contents, $matches)) {
        echo "[error] {$plan}: invalid file format\n";
        continue;
    }

    $data = json_decode($matches[1], true);
    if (!is_array($data) || !isset($data['scenes']) || !is_array($data['scenes'])) {
        echo "[error] {$plan}: invalid JSON\n";
        continue;
    }

    $removedIds = [];
    $keptScenes = [];

    foreach ($data['scenes'] as $scene) {
        $name = $scene['displayName'] ?? $scene['name'] ?? '';

        if (preg_match('/\blaundry\b/i', $name)) {
            $removedIds[] = $scene['id'] ?? $name;
            continue;
        }

        $keptScenes[] = $scene;
    }

    if (!$removedIds) {
        echo "[ok] {$plan}: no Laundry scenes found\n";
        continue;
    }

    $removedLookup = array_fill_keys($removedIds, true);

    foreach ($keptScenes as &$scene) {
        if (!isset($scene['linkHotspots']) || !is_array($scene['linkHotspots'])) {
            continue;
        }

        $scene['linkHotspots'] = array_values(array_filter(
            $scene['linkHotspots'],
            static function ($hotspot) use ($removedLookup): bool {
                $target = $hotspot['target'] ?? '';
                return !isset($removedLookup[$target]);
            }
        ));
    }
    unset($scene);

    $data['scenes'] = $keptScenes;

    if ($write) {
        file_put_contents(
            $file,
            "var APP_DATA = " . json_encode($data, JSON_PRETTY_PRINT | JSON_UNESCAPED_SLASHES) . ";\n"
        );
        echo "[write] {$plan}: removed " . count($removedIds) . " scene(s): " . implode(', ', $removedIds) . "\n";
    } else {
        echo "[dry-run] {$plan}: would remove " . count($removedIds) . " scene(s): " . implode(', ', $removedIds) . "\n";
    }
}
PHP
```

## Notes

