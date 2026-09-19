# Just describe the feature

**One-time setup:** copy the included `.cursor` folder and `PROJECT_CONTEXT.md` into your repository root and commit them so everyone gets the same setup. Preserve any existing Cursor configuration. Use Cursor Agent mode with custom subagents available.

Then anyone can simply say:

> I want a clean sales dashboard with revenue cards, a monthly chart, and a searchable orders table. Let me filter everything by date. It should look good on mobile too.

That's it. No commands, templates, role selection or configuration forms.

Cursor is instructed to automatically:

1. Work out the details from your request and existing project.
2. Have a developer implement the feature, applying the dashboard design skill when needed.
3. Have two independent agents review functionality and product/UI quality.
4. Fix issues and repeat until both approve, within the time budget.
5. Commit the approved result locally and handle Git conflicts when integrating authorized work.

The default is 50 minutes per feature and at most three review rounds. Unresolved blockers stop delivery instead of passing unfinished work. Pushing, merging and deploying use permissions already agreed with your team; local-only work needs no extra setup.

Optional team-wide preferences live in `.cursor/HACKATHON.md`. Nobody needs to edit it to start. Say “ship this” or “integrate this feature” for delivery; Cursor routes the request and applies the agreed permissions.

The included [always-on rule](.cursor/rules/hackathon.mdc) provides automatic routing using Cursor's [project rule format](https://cursor.com/docs/rules). Skills and reviewer instructions stay behind the scenes. These are agent instructions, not enforced Git protections. Format checks passed; behavior still needs a smoke test in your Cursor installation.
