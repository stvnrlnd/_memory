Deliver a morning brief for Steven based on current vault state.

1. Read today's daily note at `40_archives/daily/YYYY-MM-DD.md` (use today's date). If it doesn't exist, create it from the template at `30_resources/templates/daily-note.md`.

2. Read `90_system/context.md` for current project and business context.

3. Scan `40_archives/work_items/` for any work items with `status: in-progress` in their frontmatter.

4. Based on the above, produce a brief covering:
   - **Top priorities today** — inferred from the daily note's `## Brief` section, any in-progress work items, and known context
   - **Anything pending or unresolved** from recent daily notes (check yesterday's `## Log` if it exists)
   - **One thing to watch** — a risk, decision, or blocker worth flagging

5. Write the brief into the `## Brief` section of today's daily note, replacing the placeholder text. Use concise bullet points.

6. Display the brief in chat as well.

Keep the tone direct and practical. No fluff.
