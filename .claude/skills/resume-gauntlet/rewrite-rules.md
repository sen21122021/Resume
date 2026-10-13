# Rewrite rules for the improved resume

## 1. Truthfulness (non-negotiable)

A fabricated metric gets exposed in the first interview question about it, and it costs the candidate more than the gap it covered.

**Allowed**
- Reword, reorder, cut, merge, and tighten.
- Surface a buried accomplishment, and lead each role with its most relevant bullet.
- Describe something the candidate demonstrably did in the posting's terminology. For example, the original says "built Looker dashboards for the sales team" and the posting says "data visualization" → "Built data visualization dashboards in Looker for a 40-person sales team". The "40-person" detail is allowed **only if** the original states it.
- Make a skill explicit when the original clearly evidences it.
- Use facts the user stated in this conversation.

**Not allowed**
- Adding a skill, tool, or certification just because the posting asks for it.
- Rounding numbers up, or turning an estimate into a precise figure.
- Upgrading the role: "contributed to" or "helped" does not become "led", "owned", or "spearheaded".
- Changing titles, employers, or dates. The one exception is formatting: dates may be normalized.

**When a fix needs a missing fact,** insert `[[NEEDS INFO: <exactly what's needed, e.g. "approx. % drop in ticket backlog after the triage change">]]` in place of the fact.
- Use placeholders only where they'd change a reviewer's verdict.
- Use at most 8, and prefer fewer.
- Write the bullet so it still reads correctly if the user says the number doesn't exist and the placeholder is removed.

## 2. ATS-safe format

- A single column. No tables, text boxes, icons, photos, graphics, skill bars, or ratings.
- Nothing important in a header or footer. Contact details go at the top, in the body.
- Standard headings, in this order (drop any that don't apply):
  - Summary
  - Experience
  - Skills
  - Education
  - Certifications
  - Projects (move it above Education when it's a key part of the case, e.g. for career changers or new grads)
- The contact line holds: name, city/region, phone, email, LinkedIn, and a portfolio or GitHub link only if relevant to the role. Leave out the full street address, photo, date of birth, and marital status, unless the user says the target country expects them.
- Each role's header line: **Title**, Company, Location, `MMM YYYY – MMM YYYY` (or `– Present`). Use the same date format everywhere, and list roles in reverse chronological order.
- Where the posting uses a domain acronym or its long form, write both once, e.g. "Search Engine Optimization (SEO)", because people and parsers search for both. Leave universally known tool and technology names as they are: SQL, AWS, and Excel, not "Structured Query Language (SQL)".
- Use plain `-` bullets. In Markdown, use `#` for the name, `##` for section headings, and `###` or bold for role lines, so pandoc exports cleanly.

## 3. Length

- One page (about 450–600 words) for under about 8 years of relevant experience.
- Two pages at most (about 1,000 words) beyond that.
- Cut old or irrelevant roles to one line each, or group them under "Earlier experience".

## 4. Content

**Headline**
- Directly under the name, write a one-line positioning headline that matches the target role family, e.g. "Data Analyst | SQL · Python · Experimentation".
- It must not claim a title the candidate hasn't held.

**Summary**
- Two or three lines, tailored to *this* company and role: who they are, their strongest proof point, and what they bring to the company's current priorities from the brief.
- No clichés: "results-driven", "passionate", "team player", "detail-oriented", "dynamic", "go-getter".

**Bullets**
- Formula: strong verb + what was done + scope or how + result. Example: "Cut month-end close from 10 to 6 days by automating reconciliations in Python across 14 entities."
- Use past tense for past roles and present tense for the current role.
- Put 3–6 bullets under each recent role and 1–3 under older ones. Lead each role with the bullet most relevant to the posting.
- Quantify wherever the original or the user gives a number.
- Show outcomes, not duties. Delete "Responsible for", "Duties included", and "Worked on".

**Keywords**
- Every must-have the candidate genuinely has evidence for appears in the posting's **exact wording**, inside at least one experience bullet as well as in Skills.
- Don't stuff keywords: each term should read naturally where it appears.

**Skills**
- Group them, e.g. *Languages · Tools · Methods* or *Clinical · Systems · Certifications*.
- List the posting's must-haves first, and include only skills the candidate actually has.

**Remove**
- Objective statements.
- "References available upon request".
- Outdated or irrelevant tools.
- Soft-skill lists with no evidence.
- Hobbies, unless they're relevant to this company.

**Consistency**
- Tense, punctuation (end every bullet with a period, or none), capitalization of tool names, and date format.

## 5. Conflict resolution

Follow the decisions in the rejection report's "Where reviewers disagreed" section. If none applies:
- the gates win on being seen;
- the hiring manager wins on content priority;
- the length limits always hold.
