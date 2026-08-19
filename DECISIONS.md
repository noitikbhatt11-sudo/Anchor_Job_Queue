# DECISIONS.md — Anchor home page (Part 2)

## The idea
Anchor isn't a real product, but I didn't want it to feel like one either. It's a tool that
watches LinkedIn, Indeed, Naukri, and Wellfound for new postings and hands you one clean,
deduplicated queue instead of four tabs showing you the same nine jobs. I picked it on purpose —
it sits right next to what Acdyon actually builds: pulling real signal out of platforms that
don't make it easy. That let me design the "show the product" section around a mechanism I
actually understood, instead of faking a dashboard and hoping it read as real.

## 1. Why this direction, and what I turned down to get here
AI-assisted design has two defaults it reaches for without anyone really choosing them: a cream
background with a serif headline and a terracotta accent, or a near-black page with one neon
accent. Both are fast. Both would have taken half the time. I turned down both and built what I
think of as a "signal room" instead — dark navy-ink background, one amber accent doing all the
"look here" work, a brightened teal reserved only for source tags, and a monospace face used
nowhere except the parts of the page actually behaving like data. The test I held myself to: a
screenshot of the live feed panel and a screenshot of the nav bar should look like they came off
the same machine. If they don't, the design isn't a system, it's a coincidence.

I also committed to one theme instead of a light/dark toggle. The brief is explicit that
half-dark is worse than no dark mode, and a toggle done properly — real tokens for both states,
not inverted grays — costs more time than it was worth in this window. So I picked dark, built it
fully, and didn't hedge. One theme I'd actually stand behind felt like a more honest use of a few
hours than two themes, only one of which I'd trust in front of a recruiter.

## 2. The pipeline is the argument, not a decoration
Most three-step sections on landing pages are decorative — "01 Sign up, 02 Set goals, 03 Profit"
— where the numbers don't mean anything and the order could be shuffled without changing the
story. I refused to let that happen here, because the order in Listen → Clean → Deliver is the
actual reason Anchor is worth building:

- **Listen** is the unglamorous part — checking four sources that all behave differently,
  without looking automated. Everything downstream depends on this step not breaking.
- **Clean** is the actual product. Pulling listings is easy; collapsing the same recruiter's
  post across three boards into one entry is the hard, valuable part — and it's the exact thing
  the live feed demo shows happening, right above this section.
- **Deliver** is deliberately the plainest of the three, because by that point the work is
  already done and the copy shouldn't pretend there's more to it.

Deliver before you clean, and you've just built a faster way to see the same duplicate job eleven
times. Clean before you listen, and there's nothing yet to clean. That's also why the live feed
sits *before* this section, not after: you watch the mechanism first, then get the three words
that name what you just saw. Naming it first would've made the demo feel like an illustration of
a claim. Showing it first makes the claim feel earned — which is the whole point of the section
the brief asks for: something that shows the product instead of just describing it.

## 3. The trade-off I made on purpose
I skipped a second interactive piece — a working filter on the demo feed, for instance — to spend
that time making sure the mobile layout, focus states, motion restraint, and
`prefers-reduced-motion` handling actually held up, instead of being half-checked across five
smaller features. A broken filter under a deadline costs more credibility than a missing one ever
would. Given a real week, that filter is the first thing I'd build, followed by swapping the
fictional feed data for a screenshot of an actual pipeline run once one exists.

## 4. Why there's no fake polish
No invented testimonials, no invented user counts, no borrowed logos — and that wasn't the
default output of the tools I used, it's a call I made and then went back and checked for by
hand. The "why this exists" section is labeled as a note from the two people who'd build this,
not dressed up as a customer quote, and it says plainly that there's no real user base yet rather
than rounding up to something more flattering. The job-board names on the feed cards are text
labels describing where a fictional posting came from — not logos, and not a claim of partnership
with any of those platforms. I'd rather this page look small and honest than big and invented,
because the brief is explicit that honesty is the single biggest thing being graded, and I take
that at face value.

## 5. Where AI tools were used, and what I own
I used AI assistance to scaffold the HTML, CSS, and JS in one pass rather than typing every line
by hand — the brief says that's expected, not something to hide. What I actually did myself, and
can walk through line by line on a call: chose the palette, the type pairing, and the "signal
room" direction before any code existed; decided against a toggle and against a second
interactive filter, and can defend both calls on trade-offs alone; wrote every word of copy,
including the parts explicitly designed to *not* oversell the product; and then went back through
the built page and verified, by hand, that there's no horizontal scroll at 390px or 1440px, the
Konami-code easter egg fires and dismisses cleanly, `prefers-reduced-motion` actually turns off
the feed rotation and reveals rather than just slowing them down, and every interactive element
has a visible focus ring. None of that checklist was generated — it's the part of the job I don't
think a prompt does for you, and it's the part I'd want a teammate checking for too.

## Stack
Plain HTML, CSS, and JS — split into `index.html` and `styles.css`, no framework, no build step,
nothing to configure. It deploys as-is to GitHub Pages, Netlify, or Vercel. That was the point:
ship something finished, not something impressive-looking that needs a setup guide to run.
