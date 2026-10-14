---
name: li-plan
description: >-
  Build the week for the LinkedIn company page - what the page posts, when
  (across the buyers' time zones), who the page and its staff engage with,
  and which employees reshare. Use when the user says "plan my week", "plan
  the page", "what should we post", "content calendar", "we have nothing to
  post about", or wants a posting schedule and an engagement list.
---

# li-plan

The control room for the company page. Everything else in this pack executes;
this decides what gets executed. Run it once a week, on the same day.

## Input

Read `.claude/linkedin/voice.md` (brand voice, buyers, markets,
certifications, off-limits claims) and `log.md` if it exists - the plan
should not repeat a theme or a product from the last fortnight. If voice.md
is missing, ask the user to fill it in first.

Then ask for one batch of what actually happened this week, because that is
where company posts come from:

1. Production and QC - a batch finished, a defect caught, a new process,
   a machine, an audit.
2. Shipments and orders - where things went (country, buyer type, not name),
   volumes if shareable.
3. Product - new item, new finish, new packaging, catalogue update.
4. People - a craftsman, a long-serving team member, training, a visitor.
5. Events - trade shows, buyer visits, holidays and factory closures.

Also ask for 10-20 accounts worth being visible to: distributors, dental and
surgical associations, trade show pages, buyers' companies.

## What to post

Three to five posts a week. Four is the working default. A gap of more than
ten days reads to a buyer as a supplier that might not be trading.

Mix across the week, never two of the same type back to back:

| type | share | job |
| --- | --- | --- |
| **Proof** | 1 per week | QC, audit, certificate, shipment - with a number |
| **Product** | 1 per week | one instrument or range, shown properly, what it is for, who buys it |
| **Educate** | 1 per week | something a buyer can use today: care and sterilisation, steel grades, how to spot a bad hinge, how to brief an OEM order |
| **Factory / people** | 1 per fortnight | the craft and the team behind the product - a real person, a real step |
| **Offer** | 1 per fortnight | catalogue, OEM / private label, trade show meeting, sample request, said plainly |

At most one in four posts is a direct offer. A page that only sells gets
scrolled past; a page that proves and teaches gets the enquiry.

For each slot give: the type, the buyer it is written for (distributor /
hospital / clinic), the market if it is market-specific, the angle drawn from
what actually happened this week, the hook number from `li-post/hooks.json`,
and the visual. Not a topic - an angle. "Scissors" is not a plan. "The 3
checks every Metzenbaum gets before it is boxed" is a post.

## When to post

The page is run from Pakistan (PKT, UTC+5) but the buyers are spread across
the UK, UAE, Nigeria, Bangladesh and the USA. Anchor times to the buyer, then
convert to PKT for the user.

| window (PKT) | who is at a desk |
| --- | --- |
| **12:00-14:00** | UK and Nigeria morning, UAE midday, Bangladesh afternoon. The default slot - it reaches four of five markets. |
| **17:00-19:00** | US East Coast morning (17:00 in US summer time, 18:00 in winter). Use for one US-focused post a week. |
| **09:00-11:00** | UAE and Bangladesh morning. Good for Gulf- or Bangladesh-specific posts. |

- Tuesday to Thursday are the strongest days for all five markets.
- Friday is the weekend in Bangladesh and a short day for many Gulf
  businesses - avoid it for posts aimed there.
- Watch the calendar: Eid, Ramadan working hours, UK bank holidays, US
  Thanksgiving. Note them in the plan; post less, not nothing.
- UK and US clocks change in March/April and October/November; Pakistan's do
  not. Recheck the PKT conversion when they do.

State this plainly: **the hour matters far less than whether the first line
and the visual are good.** If the page's posts are not working, fix the hooks
before the schedule.

## Who to engage with

A company page can comment as the page, but people's comments travel further.
Split engagement between the page and two or three staff:

- **5 buyers** - distributors, hospital groups, clinic chains. Comment for
  weeks before any DM. Never pitch in a comment.
- **3 industry** - associations, trade shows (dental and medical expos the
  buyers attend), industry media. Comment as the page.
- **2 peers** - non-competing suppliers in the same channels (sterilisation,
  dental consumables). They reshare and introduce.

15-20 minutes a day, before the post goes out.

## Employee amplification

Most people will see a company post because a person reshared it. Each week:

- Name 3-5 staff (sales, export, QC lead, a director) who reshare that week's
  posts with a line of their own - `/li-post` writes a suggested line.
- Use LinkedIn's page feature to notify employees about a post when it is
  available on the page and worth it - once or twice a week, not every post.
- Check that new staff list the company as their employer linked to the page.

## Output

```
WEEK OF OCT 19                         (times in PKT)

MON  engage only  (20 min, list below)
TUE  12:30  PROOF     distributor   #2  Number Reveal  - forceps batch QC, reject count
            visual: rejected vs passed forceps, plain bg
WED  12:30  EDUCATE   clinic        #21 Direct Value   - 4 signs a scaler needs replacing
            visual: carousel (/li-carousel)
THU  18:00  PRODUCT   hospital, US  #12 Comparison     - new tungsten carbide needle holders
            visual: macro of the TC insert
FRI  -      (Bangladesh weekend, Gulf short day)
SAT  -
SUN  -

RESHARE  Tue: export manager, QC lead   Wed: director   Thu: US sales
ENGAGE   (5 buyers / 3 industry / 2 peers)
  ...

Say "write Tuesday" and I will draft it.
```

Write the plan to `.claude/linkedin/plan.md` so the other skills can read it.
Nothing is scheduled or posted anywhere - this is a plan, and the user runs
it.
