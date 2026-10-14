---
name: li-profile
description: >-
  Score a LinkedIn profile out of 100 against a 12-part rubric and rewrite the
  parts that lose points - headline, about, experience, featured, banner. Use
  when the user says "optimize my profile", "score my LinkedIn", "rewrite my
  headline", "fix my about section", or pastes their profile and asks how it
  reads. Also scores a LinkedIn Company Page against a separate 12-part
  company rubric when the user says "company page", "score our page", "fix
  our tagline" or pastes a company page's About/overview.
---

# li-profile

A profile is not a resume. A resume answers "what have you done". A profile
answers "should I message this person", and it answers it in about four
seconds, from the headline and the first two lines of the about.

## Which rubric

- The user says **"company page"**, "our page", "the DSS page", or pastes a
  tagline / overview / specialties: go to **Company page mode** below and use
  `company-rubric.json`. Do not score a company page against the personal
  rubric - it has no headline, photo or recommendations.
- Anything about their own profile: the personal flow that follows, with
  `rubric.json`.

If it is unclear, ask once: "your personal profile or the company page?"

## Input

Ask the user to paste: headline, about section, current role and the last two
experience entries, plus whether they have a banner and featured section. A
screenshot of the top card is enough for the first pass. Do not log into
LinkedIn on their behalf.

## Score it

Read `rubric.json` in this folder. Twelve items, 100 points, each with what
full marks looks like. Score every item, show the table, and give the total.
Be honest - most profiles land in the 30s and 40s on the first pass, and a
generous score is useless.

```
PROFILE SCORE  41/100

  headline            3/12   job title only, no outcome, no audience
  about first 2 lines 2/10   opens with "passionate about"
  about body          4/10   history, not offer
  featured            0/8    empty
  banner              0/6    default blue
  ...
```

## Then rewrite, in this order

Fix in descending order of points lost. Do not rewrite everything at once -
the user has to actually paste each of these in.

**1. Headline (220 characters).** The formula that works:
`{what you do for whom} | {proof} | {how to start}`. Not your job title. Not
"Helping X do Y" as the first three words, which every second profile now
opens with. Give three options.

**2. About, first two lines.** Everything after line 2 is behind "see more" on
mobile, so those two lines are the whole about section for most readers. They
must state who you help and what changes. No "passionate", no "results-driven",
no third-person bio, no opening with your own name.

**3. About body.** Written to one reader, in the second person. Structure:
the problem they have, what you do about it, one piece of proof with a number,
what to do next. Under 1,400 characters even though the limit is 2,600.

**4. Featured.** Three items: the best post, the proof asset, the way to
contact. An empty featured section is eight points and the only place on the
profile you fully control.

**5. Experience.** Each role gets one line of scope and two to three bullets
that are outcomes with numbers, not duties. Cut anything older than ten years
to a single line.

**6. Banner.** One sentence of positioning and one way to reach you. The
default blue gradient is the clearest signal on the page that nobody is home.

## Output

Score table, then the rewrites as copy-ready blocks in fix-first order, each
one already run through `/li-human`. Re-score at the end and show the delta
honestly - if the rewrite gets to 88 and not 98, say 88, and say what the
remaining points need (usually recommendations, a real banner and posting
history, none of which a rewrite can create).

Nothing is saved to LinkedIn by this skill. The user pastes each section in.

## Company page mode

A company page is not a brochure. A procurement manager, a hospital buyer or
a clinic owner lands on it to answer one question: is this supplier real,
certified and still trading. They answer it from the banner, the tagline, the
first two lines of the overview and the date of the last post.

### Input

Ask the user to paste: tagline, the full About/overview, specialties, website
and custom button setting, industry/size/locations, any showcase pages, and
the dates and topics of the last 12 posts (or a screenshot of the page and the
Posts tab). Ask roughly how many employees list the company as their current
employer. Read `.claude/linkedin/voice.md` - it holds the brand voice,
certifications, markets and off-limits claims.

### Score it

Read `company-rubric.json` in this folder. Twelve items, 100 points. Score
every item, show the table, give the total. Same honesty rule as the personal
rubric: a page that was set up once and left alone scores in the 30s.

```
COMPANY PAGE SCORE  44/100

  tagline              3/10   slogan, no product, no buyer
  about_overview       5/12   founding story above the fold, no certs
  posting_frequency    2/12   last post 5 weeks ago
  employee_connection  2/10   page shows 4 employees
  cover_banner         0/8    default
  ...
```

### Then rewrite, in this order

Fix in descending order of points lost, as with the personal profile. The
usual order for a manufacturer/exporter:

**1. Tagline (120 characters).** `{what we make} for {which buyers} |
{proof: certification / markets / years}`. Give three options. Brand voice,
"we" where a verb is needed.

**2. About, first two lines.** Product range, buyer type and the
certification that removes risk. Nothing about the founding year up here.

**3. About body.** What we make, where, the quality system, the markets we
ship to, OEM/private label if offered, how to request a catalogue or quote.
Under 1,500 characters. Close with one action.

**4. Banner.** One line of positioning, one real product or factory image,
certifications in plain text. Give the copy and a layout brief, 1128x191.

**5. Specialties.** 10-20 terms buyers actually search, grouped as products,
capabilities, standards.

**6. Website and button.** Which button, which URL, and the UTM string.

**7. Page details, showcase pages, trust signals.** A short checklist, not
prose. Say plainly if showcase pages should be deleted rather than fixed.

**8. Posting and employees.** These cannot be fixed by a rewrite. Hand
posting cadence and content mix to `/li-plan`, and give the employee fix as a
three-step checklist (link the right page as employer, matching titles, a
weekly reshare habit for 3-5 named roles).

### Rules for company pages

- **Medical device claims stay inside the certificate.** ISO 13485, CE and
  UKCA are stated exactly as held and only for the products they cover. Never
  add FDA, "approved", "hospital-grade", clinical outcome or "best quality"
  claims unless voice.md lists them as true. If unsure, leave
  `{{confirm claim}}` and flag it.
- **No customer, distributor or hospital named** unless voice.md says there is
  permission.
- Brand voice from voice.md, not the user's personal voice.

### Output

Score table, then the rewrites as copy-ready blocks in fix-first order, each
run through `/li-human`. Re-score at the end and show the honest delta -
posting history and employee connection usually cap a rewrite-only score
around 70-75, and say so.

Nothing is saved to LinkedIn by this skill. The user pastes each section in.
