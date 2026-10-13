# Resume Gauntlet

You apply to dozens of jobs and never find out why you were rejected. This Claude Code workflow puts your resume in front of **seven Claudes that try to reject it first**. You get every reason, in their own words, then an improved resume with every fixable mistake fixed.

## The seven reviewers

| Stage | Reviewer | The question they answer |
|---|---|---|
| Gate 1 | **ATS screener** | Does a human ever see this? Checks parsing, knockout filters, and keyword coverage. |
| Gate 2 | **Hiring manager** | Does this get the interview? |
| Panel | **Direct manager** | Do I want to work with this person every day? |
| Panel | **Rival applicant** | How does the strongest competitor beat you? |
| Panel | **CEO** | Does this hire move the numbers we care about? |
| Panel | **Recruiter** | Does this pass the 7-second skim? Are there red flags I can't defend? |
| Panel | **Future teammate** | Are the claims credible, and what would I grill you on? |

All seven read the resume **alone and in parallel**: no reviewer sees another's opinion. The results are then laid out as a funnel, so you can see exactly where your resume would have died.

After that, the workflow:
1. merges every finding into a single ranked **rejection report**;
2. rewrites the resume, which must stay **truthful** (it never invents metrics, titles, or skills) and **ATS-safe**;
3. **re-screens** the new version through both gates to show the before and after.

## Setup

1. Install [Claude Code](https://code.claude.com). The CLI, the desktop app, and claude.ai/code all work.
2. Clone this repo and open it in Claude Code:
   ```bash
   git clone https://github.com/sen21122021/Resume.git
   cd Resume
   claude
   ```
3. Optional, but recommended:
   - [`pdftotext`](https://poppler.freedesktop.org/) (from poppler) shows exactly what a dumb parser sees in your PDF.
   - [`pandoc`](https://pandoc.org/) reads .docx resumes and exports the improved resume to .docx.

   On macOS: `brew install poppler pandoc`.

## Usage

Put your resume in `resume/`. It can be a PDF, DOCX, Markdown, or text file. Then run one of these:

```text
/resume-gauntlet resume/my-resume.pdf https://boards.greenhouse.io/acme/jobs/123 "Acme Corp"
```

```text
/resume-gauntlet resume/my-resume.pdf jobs/stripe-pm.md Stripe
```

```text
/resume-gauntlet
```

With no arguments, it uses the one file in `resume/` and asks you to paste the job posting.

- **Arguments:** these can come in any order. Quote company names that contain spaces. If you leave the company out, it's read from the posting.
- **Postings behind a login:** LinkedIn and Indeed often block fetching, so paste the posting text instead.
- **`--full-rescreen`:** re-runs all seven reviewers on the improved resume, not only the two gates.
- **Automatic use:** you can also just ask, e.g. "run my resume through the gauntlet for this job", and Claude will use the workflow.

## What you get

Everything lands in `applications/<date>-<company>-<role>/`:

```
resume-improved.md      ← the rewritten resume
resume-improved.docx    ← if pandoc is installed
rejection-report.md     ← scoreboard, why you'd be rejected, what was fixed, open questions
changelog.md            ← every issue → the exact change made
reviews/                ← the seven raw reviews, plus the re-screens
company-brief.md        ← what the reviewers knew about the company
job-description.md, resume-original.md, …
```

## Filling in the questions

Some fixes need facts only you know, like "by how much did this reduce costs?" The workflow never makes these up. It leaves a placeholder such as `[[NEEDS INFO: approx. % reduction in close time]]` and asks you at the end. Reply with the answers, or with "I don't have that number", and it finishes the resume and re-screens it.

**Don't send a resume that still has `[[NEEDS INFO]]` placeholders in it.**

## Privacy

This repository is **public**. `resume/`, `jobs/`, and `applications/` are gitignored, so your resume and results never get committed. In a Claude Code on the web session, the container is temporary: paste or attach your resume in the chat, and download the improved files before the session ends. If you make the repo private and want results kept in git, delete those lines from `.gitignore`.

## Customizing

- **Reviewers:** edit the personas in `.claude/agents/`. Each one is a plain Markdown prompt.
- **Writing rules:** change them in `.claude/skills/resume-gauntlet/rewrite-rules.md`, e.g. page length or regional conventions such as a CV with a photo.
- **Adding a reviewer:** create a new agent file, then add it to the table in Step 2 of `.claude/skills/resume-gauntlet/SKILL.md` and to the scoreboard in `report-template.md`.

## Cost

One run is 9 reviewer passes (7, plus 2 in the re-screen) and a short company research step. It takes about 5 minutes. A test run on a one-page resume cost about $1.50 in API-equivalent usage. On a Claude subscription it counts toward your normal Claude Code usage.
