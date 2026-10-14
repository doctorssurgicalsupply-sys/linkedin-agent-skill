---
name: li-carousel
description: >-
  Build a LinkedIn document post (carousel) - slide-by-slide copy, the cover
  that earns the swipe, and the PDF to upload. Use when the user says
  "carousel", "document post", "slides for LinkedIn", "turn this into a
  carousel", or has a list-shaped idea that would die as a text post. Written
  for the company page: brand voice ("we"), B2B buyers, logo and website on
  every slide.
---

# li-carousel

Document posts are the highest-dwell format on LinkedIn, because a swipe is
counted and a scroll is not. The format rewards one idea broken into steps.
It punishes a text post cut into pieces.

This pack runs a **company page**, so every carousel is for a B2B buyer - a
distributor, a hospital procurement team or a clinic owner - and speaks as
the brand. Read `.claude/linkedin/voice.md` first for the voice, buyers,
certifications and claims that are off limits.

## What works for a manufacturer

Carousels are where a supplier can show the work a buyer never sees:

- **Process** - how one instrument is made or inspected, step by step.
- **Buyer guides** - how to spot a bad hinge, steel grades explained, care
  and sterilisation do's and don'ts, what to send us for an OEM quote.
- **Range overviews** - one family (extraction forceps, needle holders) with
  what each pattern is for. One family per deck, not the catalogue.
- **Ordering** - from enquiry to dispatch: samples, MOQ, documents, lead time.

A carousel that is just the product catalogue in PDF form is an ad, and gets
treated like one. Pick the buyer the deck is for and say it in the receipt.

## When to use it instead of a text post

Use a carousel when the idea has **sequence** - steps, a countdown, a
before/after progression, a framework with parts. Use a text post when the
idea is one claim. Splitting one claim across eight slides is the most common
way carousels fail, and if that is what the user has, say so and hand them to
`/li-post`.

## Structure

8-12 slides. Under 8 is a text post. Over 12 and the completion rate falls off
a cliff.

```
1        COVER      the hook, 6 words or fewer, plus one line of promise
2        THE STAKE  why this matters, in one sentence
3-N      ONE IDEA PER SLIDE. A headline of 3-7 words, and at most 25 words
                    under it. If a slide needs a paragraph, it is two slides.
N+1      RECAP      the whole thing as a list, so the screenshot is useful
LAST     CTA        one action: request the catalogue, ask for a quote or
                    samples, follow the page. One. Website on this slide.
```

## Slide copy rules

- **Slide 1 is 80% of the result.** Six words. Big. The rest of the deck
  cannot save a cover nobody swipes.
- **Number every slide** (3/10). Completion goes up when people can see the
  end.
- **No slide is a paragraph.** If you cannot say it in 25 words, split it.
- **The recap slide is the one people screenshot.** Make it standalone.
- **Logo and website on every slide**, small, bottom corner. Screenshots
  travel without you, and a buyer forwarding slide 6 to their boss needs to
  know whose it is.
- **Real photos only.** The company's own instruments and factory, shot on a
  plain background. No stock surgeons, no AI-generated instruments.
- **Claims stay inside the certificate.** Certifications are stated in text
  exactly as voice.md lists them. Do not paste CE or UKCA marks as decoration
  on generic slides; the marks belong with the products they cover. No
  "approved", "best quality" or clinical-outcome claims unless voice.md says
  they are true. If unsure, leave `{{confirm claim}}`.
- **No customer named** unless voice.md says there is permission.

## Making the PDF

LinkedIn wants a PDF, 1080x1350 (4:5) for maximum feed real estate, under
100MB, under 300 pages. Build it as HTML and print to PDF:

```bash
# one page per slide, 1080x1350, no margins
# then: Chrome headless --print-to-pdf, or any HTML-to-PDF you already use
```

Write the HTML with one `<section>` per slide, `width:1080px; height:1350px;
page-break-after:always`, a single accent colour, and type no smaller than
28px - people read these on a phone at thumbnail size. Use the brand colours
and fonts from voice.md (or a brand skill / design system in this project);
do not invent a palette. Clinical, clean, plenty of white space - the
instruments are the visual.

## Output

The slide-by-slide copy first, as a numbered list the user can read in ten
seconds. Then the accompanying **post text** - a carousel still needs 2-3
lines above it, which is the actual hook in the feed, in the brand voice -
plus a one-line employee reshare caption as in `/li-post`. Run all of it
through `/li-human`. Note which slides need a real photo and what it should
show. Then build the PDF only if the user approves the copy.

Nothing is uploaded to LinkedIn. The user posts the PDF themselves.
