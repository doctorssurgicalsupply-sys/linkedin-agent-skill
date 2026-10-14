---
name: li-post
description: >-
  Write a LinkedIn company page post from a raw idea using 21 proven hook
  formulas, in the brand's voice ("we"), for a B2B buyer audience, humanized
  so it does not read as AI. Use whenever the user wants a LinkedIn post, a
  hook, a draft for the page, "post about X", "turn this into a LinkedIn
  post", or asks for hook options. Produces three hook options, one full
  draft, a visual brief, an employee reshare line, and a copy-ready block that
  is never published without an explicit yes.
---

# li-post

Turns one raw idea into a post for the company page that a buyer would stop
for: a distributor's purchasing manager, a hospital procurement officer, a
dental clinic owner. The page speaks as **we**. Nobody on the page has a
personal brand to build. The job is to make a buyer trust the supplier a
little more each week.

## Before you write

1. Read `.claude/linkedin/voice.md`. It is the **brand** voice: how the
   company talks, who the buyers are, which markets, which certifications are
   held, and which claims are off limits. If it does not exist, stop and ask
   the user to fill it in first (or run the voice interview). Do not invent a
   brand voice.
2. Read `hooks.json` in this folder. The formulas are written in the first
   person singular. On a company page, translate them: "I" becomes "we", or,
   better, the hook is rewritten around the buyer's problem. "I sent 400 cold
   DMs" becomes "We inspected 4,000 forceps last month. 37 failed." A formula
   that only works as a personal confession (#3 Mistake, #9 Cold Open told as
   a private story) needs a real company story behind it or should not be used.
3. If the idea is thin - "post about our scissors" - do not pad it. Ask one
   batched question: what actually happened (an order shipped, an audit
   passed, a defect caught, a new line launched), for which kind of buyer, and
   is there a number. A post needs one specific true thing.

## Who is reading

Write for one buyer at a time. Before drafting, decide which one:

| buyer | what they care about |
| --- | --- |
| **Distributor / importer** | consistency batch to batch, lead time, MOQ, documentation for their regulator, private label/OEM, margin |
| **Hospital / procurement** | certification scope, traceability, reprocessing and sterilisation compatibility, tender paperwork, reliability of supply |
| **Dental clinic owner** | how the instrument feels and lasts, sharpness, price per year of use, where to buy locally |

Name the buyer in the receipt. A post that tries to talk to all three talks to
none.

Markets differ. A UK or US buyer wants documentation and compliance stated
precisely. Gulf, Nigerian and Bangladeshi buyers often weigh responsiveness,
lead time and supplier reliability more heavily. Do not stereotype in the
copy; just choose the proof that matters to the buyer named.

## The shape

Company page posts get less organic reach than personal posts, so the first
line and the visual carry more weight, and employees resharing is how most
people will see it.

```
Line 1     the hook. Alone. Survives truncation at ~140 chars on mobile.
           About the buyer's problem or a concrete fact, not about "us".
Line 2     the payoff of line 1, not setup for line 3.
Body       short paragraphs, 1-3 lines each, blank line between.
           One proof point: a number, a process step, a certificate.
The turn   what this means for the buyer.
Close      one action: request the catalogue, ask for a quote, DM the page,
           or one specific question. Never two.
```

Length: 600-1,200 characters. Company pages earn less "see more" patience
than a person does.

## The loop

**1. Pick three hooks, not one.** Run the idea through `hooks.json`, translate
to the brand voice, and choose three that genuinely fit. Different formulas.
Show them as three numbered lines and say which you would ship and why.

**2. Draft the full post** on the strongest hook.

**3. Visual brief.** Every company post ships with a visual. Say what it is in
one or two lines: a real photo of the instrument on a plain background, a
close-up of the laser marking, a short clip from the polishing line, or a
carousel (hand off to `/li-carousel` if the idea has steps). Never a stock
photo of a smiling surgeon.

**4. Employee reshare line.** One or two lines, first person, that a sales or
export team member could paste when they reshare from their own profile. It
should add something, not repeat the post ("Packed this one myself, 1,200
pieces to Lagos").

**5. Humanize it.** Run the post and the reshare line through `/li-human`
before showing them.

**6. Print the block.** Copy-ready, in a fenced block, exactly as it should be
pasted. Then:

```
POST READY
buyer:     distributor (UK)
hook:      #2 Number Reveal
length:    880 characters
visual:    close-up of 3 rejected forceps next to 1 passed, plain grey bg
reshare:   1 line for export team (below)
humanizer: 5 artefacts stripped, human score 82 PASS
post at:   Tuesday 13:00 PKT (from your plan)

Reply "yes" to log it, or tell me what to change.
```

**7. Never publish.** This skill produces text. The user posts it. On "yes",
append the post to `.claude/linkedin/log.md` with the date, the buyer, the
hook used and the first line, so `/li-audit` has a history to work from.

## Rules that make the difference

- **Buyer first, company second.** "We are proud to announce" is dead on
  arrival. Lead with what changes for the buyer.
- **One idea per post.** If the draft has two, it is two posts.
- **Numbers over adjectives.** "Inspected under 10x magnification" beats
  "rigorous quality". If no number was given, ask for one.
- **Claims stay inside the certificate.** ISO 13485, CE, UKCA and any other
  registration are stated exactly as voice.md lists them, and only for the
  products they cover. No "FDA approved", "hospital-grade", "best quality",
  "No.1" or clinical-outcome claims unless voice.md says they are true and
  allowed. If unsure, leave `{{confirm claim}}` and flag it.
- **No customer named** - distributor, hospital or clinic - unless voice.md
  says there is permission. "A distributor in Manchester" is fine.
- **No price in the post** unless the user asks. "Request a quote" is the CTA.
- **No festival-greeting-only posts.** If the user wants one, tie it to
  something true about the team or the work.
- **No engagement bait.** "Thoughts?" and "Agree?" are dead.
- **Three hashtags maximum**, at the bottom, real categories buyers follow
  (#DentalInstruments, #SurgicalInstruments, #MedicalDevices), never
  #Sialkot #Quality #Best.
- **No links in the post body.** Put the catalogue or quote link in the first
  comment and say so in the receipt.
- **Never fabricate.** No invented order volumes, customers, audit results,
  countries or outcomes, even as placeholders. If a number is needed and
  unknown, leave `{{number}}` in the draft and flag it.

## Example

```
/li-post our QC team caught a hinge defect in a batch of extraction forceps before dispatch
```

```
BUYER  distributor / importer

HOOKS
1. #2  Number Reveal   We inspected {{number}} extraction forceps last week. {{number}} never left the building.
2. #12 Comparison      A forceps that passes a visual check vs one that passes ours. Same photo, different hinge.
3. #17 Time Anchor     The defect took seconds to find on our bench. In a clinic it shows up months later.

Shipping #1: the reader is buying consistency, and a rejection count proves it.
Need from you: the batch size and the reject count.
```
