# Idea Dump — Atlantis World-Building

Capture and file a world-building idea into the Atlantis knowledge base.

## Step 1 — Source

Ask the user:
> "Do you want to (a) dictate a new idea, or (b) pull an existing GitHub issue?"

**If dictating (a):**
- Listen to everything the user tells you without interrupting. Only ask a follow-up if something is genuinely ambiguous.
- Create a GitHub issue in `nlsui/atlantis` with a clear title and the full idea in the body, organized but faithful to what was said.
- Note the issue number for later.

**If existing issue (b):**
- Ask for the issue number.
- Fetch it: `gh issue view <number> --repo nlsui/atlantis`
- Note the issue number for later.

## Step 2 — Analyze

Read the Atlantis file structure and relevant existing files to understand what's already there. The repo lives at `C:\Users\Marius Standard\workspace\smooth-sloperator\Atlantis`.

Determine which files should be updated or created based on the idea. Consider all areas: stories (seeds, plotlines, characters, scenes, drafts), characters, geography, history, society, systems, open-questions.

## Step 3 — Present plan

Present a numbered list to the user. Each line is one file with a single sentence describing what you intend to add or change. Example format:

> 1. `stories/plotlines/relic-lineage.md` — Create new file: a plot arc about a relic passed patrilineally, lost, then rediscovered through a secret matrilineal chain.
> 2. `society/inheritance.md` — Add a note that inheritance customs may differ by gender for sacred objects.

Wait for the user to approve or reject individual items. Adjust if needed.

## Step 4 — Execute

Once approved:
1. Make all file changes.
2. Commit with a message that references the issue: `git commit -m "..."` — include `Closes #<number>` in the body.
3. Push to master: `git push`
4. Get the commit hash: `git rev-parse HEAD`
5. Close the issue: `gh issue close <number> --repo nlsui/atlantis`
6. Comment on the issue linking the commit:
   `gh issue comment <number> --repo nlsui/atlantis --body "Implemented in commit nlsui/atlantis@<hash>"`
