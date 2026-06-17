# Uncle Inc. — Build Plan

## 1. PRODUCT

Uncle Inc. is an AI-assisted MVP validation and launch platform for non-technical, solo, or first-time founders. The core value proposition: instead of spending months (and thousands of dollars) on developers to find out an idea doesn't work, founders can describe their idea in plain language, get an AI-generated clickable prototype, run it in front of real users, collect structured validation signals (sign-up intent, click-through, qualitative feedback), iterate on what the AI learns, and deploy a working landing page or MVP — all in one continuous flow. It solves the classic "I have an idea but can't code and don't want to waste six months and $30k to find out nobody wants it" pain, and replaces the cobbled-together stack (Notion + Figma + Carrd + Typeform + a friend who codes) with a single tool that gives a non-technical founder a defensible validation loop before they commit to building.

## 2. WHO IT'S FOR

The ICP is a **time-poor, non-technical, first-time or solo founder** — often a domain expert leaving a corporate job, a designer/PM with a side idea, or a technical-adjacent operator who can ship landing pages but cannot (and does not want to) build a real backend. They are skeptical of "AI builds your startup in 60 seconds" hype, allergic to jargon, and price-sensitive early on ($49/mo ceiling). They want signal, not toys. The product reflects this in three ways: (1) the marketing site leads with the **outcome** ("Validate before you build") not the feature list, (2) the design is **dark and analytical** — like a trading terminal or Linear — to signal "serious tool for people who measure things" rather than "fun AI toy", (3) the pricing has a genuine free Explorer tier with no credit card so the skeptical founder can verify the product works before paying, and the headline CTAs frame everything as **early access / waitlist** because the product is pre-launch and we will not pretend otherwise.

## 3. LOOK & FEEL

### Visual system

- **Vibe / positioning:** Signal Lab. Dark, analytical, precise, slightly futuristic. Reads as a tool for people who take ideas seriously — closer to Linear, Vercel, or a quant terminal than to a consumer SaaS landing page. Restrained glow accents (indigo / cyan / teal) on an ink-black canvas; no gradients-as-decoration, no playful illustrations, no emoji.
- **Color palette (Tailwind tokens):**
  - `ink` `#0a0a0f` — primary background
  - `ink-2` `#12121a` — elevated surfaces (cards, nav)
  - `ink-3` `#1a1a26` — hover/borders
  - `border` `#262633` — hairline dividers
  - `muted` `#8b8b9a` — secondary text
  - `text` `#e8e8ef` — primary text
  - `indigo` `#4f46e5` — primary accent (CTAs, focus, beam lines)
  - `cyan` `#06b6d4` — secondary accent (data viz, hover glow)
  - `teal` `#14b8a6` — tertiary accent (success, "validated" state)
- **Typography:**
  - Headings: `Space Grotesk` 500/600, tight tracking (`-0.02em` on h1, `-0.01em` on h2-h3)
  - Body: `Inter` 400/500 (loaded from `next/font/google` as a secondary face — Space Grotesk is too wide for body copy at 16px; Space Grotesk is reserved for display only)
  - Mono: `JetBrains Mono` 400/500 — used for code, metrics, labels, eyebrow text
- **Spacing / layout:** Max content width `1180px`, generous vertical rhythm (sections are `py-24`/`py-32` on desktop), 12-column grid on desktop, single column on mobile. Cards are `rounded-xl` with `border border-border bg-ink-2/60` and `backdrop-blur`. Section eyebrows are mono uppercase (`text-xs tracking-[0.2em] text-cyan`).
- **Key components:** `BeamLine` (horizontal 1px gradient line used as section dividers and a recurring motif), `GlowButton` (indigo background with a subtle `box-shadow: 0 0 24px rgba(79,70,229,0.35)` and a 1px teal inner border on hover), `FeatureCard` (icon in a 40px square with a 1px border and tinted glow, title, body, 1-line mono meta tag), `WaitlistForm` (email input + button, inline below hero), `FAQAccordion` (mono `+`/`–` toggle, content reveals with 200ms ease), `PricingCard` with a single highlighted "Most popular" tier that has a teal hairline border and a faint cyan glow.
- **Iconography:** Lucide icons (`lucide-react`) at `stroke-width={1.5}` — Zap, Users, BarChart3, Compass, RefreshCw, Rocket for the 6 features. No filled illustrations, no stock photos, no 3D renders.
- **Imagery:** None on the marketing site. The product is the visuals. Where a "screenshot" would normally go, we use a **terminal-style mock** — a monospace card with fake-but-honest "what you'd see" copy (e.g. `> idea: "AI dunning tool for freelancers"` followed by generated validation prompts). Marked visually as a preview, not a screenshot of a real working product.
- **Motion:** Subtle and on-purpose. (1) On load, a 1px indigo beam line draws from left to right across the hero (600ms). (2) Feature card hover: `border-color` transitions to `cyan`, a 1px teal underline appears at the bottom, the icon's glow intensifies. (3) Section reveals on scroll via `framer-motion` `whileInView` with 8px y-offset and 400ms duration. No parallax, no bouncing, no scroll-jacking.

### Screens, top to bottom

1. **Nav** — Sticky, `bg-ink/80 backdrop-blur-md border-b border-border`. Left: a small beam-line glyph (a 24px horizontal indigo→cyan gradient line) + wordmark `Uncle` in Space Grotesk 600 + `.` in cyan. Right: `Features`, `Pricing`, `FAQ` (mono 12px, `text-muted hover:text-text`) + a `Join Waitlist` glow button. On mobile: hamburger opens a full-screen overlay with the same links stacked.
2. **Hero** — Eyebrow `// SIGNAL LAB · EARLY ACCESS` (mono, cyan). H1 in Space Grotesk 600, 64–80px desktop / 40px mobile: `Validate Your Startup Idea Before You Build It.` Subhead in `text-muted`, max-width 560px: `AI-assisted MVP validation for non-technical founders. Describe the idea, test it with real users, and only build what people actually want.` Below: `WaitlistForm` (email input 360px wide, `Join Waitlist` button). Below the form: a one-line micro-disclaimer in `text-muted text-xs`: `No credit card. Early access opens to waitlist members first.` A `BeamLine` divider below the hero.
3. **Social proof strip (honest version)** — Single line, mono 12px, `text-muted`, no logos, no numbers: `Built for solo founders, domain experts, and first-time operators. Currently in private beta.` This replaces the "used by 10,000 teams" strip with something truthful.
4. **Features** — Section eyebrow `// CAPABILITIES`, h2 `Everything you need to go from idea to validated MVP.` 6 cards in a 3×2 grid (2×3 on tablet, 1×6 on mobile), each with: mono index `01`–`06` in `text-cyan`, icon in a 40px bordered square, title (Space Grotesk 500, 20px), one-paragraph body (`text-muted`, 15px), 1-line mono meta tag (e.g. `~ 2 min to first prototype`). Card titles: `AI Prototyping`, `Real User Testing`, `Launch Analytics`, `Guided Validation`, `Rapid Iteration`, `One-Click Deploy`.
5. **How it works** — 3 numbered steps, vertical on mobile / horizontal on desktop, each step is a 1px-bordered card with a mono `01/02/03` index, a one-line title, a 2-sentence description, and a tiny terminal-style preview block with honest example copy (e.g. `> describe your idea` → 3 generated next-step prompts). Steps: (1) `Describe your idea` (plain language), (2) `Run it past real users` (share a link, collect signals), (3) `Decide what to build` (see what validated, deploy the winner).
6. **Pricing** — Section eyebrow `// PRICING`, h2 `Simple pricing. Start free. Pay only when you validate.`, sub `No per-seat fees. No usage traps. Cancel anytime.` 3 tiers in a row (stacks on mobile):
   - **Explorer** — `$0 / mo` — `For curious founders kicking the tires.` — 1 active project, 1 AI prototype / month, 25 validated-user responses / month, community support. CTA: `Start free`.
   - **Builder** — `$49 / mo` — `Most popular` teal hairline + glow. `For founders ready to test a real idea.` — 5 active projects, 20 AI prototypes / month, 500 validated-user responses, real-user testing suite, landing page deploy, email support. CTA: `Join waitlist`.
   - **Team** — `$149 / mo` — `For two-person founding teams.` — Unlimited projects, unlimited prototypes, 5,000 responses / month, 3 seats, shared workspace, priority support. CTA: `Join waitlist`.
   - Below the cards: a one-line honest disclaimer: `Prices shown in USD. Final pricing may change before public launch.`
7. **FAQ** — Section eyebrow `// QUESTIONS`, h2 `Frequently asked.`, 5 questions in an accordion:
   - `What exactly does the AI build?` — A clickable prototype (no-code, web-based) plus a shareable landing page, generated from your plain-language description. You can edit both in the browser.
   - `Do I need to know how to code?` — No. The platform is built for non-technical founders. If you can write a tweet, you can describe your idea.
   - `How is this different from a no-code tool?` — No-code tools give you a blank canvas. Uncle generates the prototype from your description, then helps you measure whether real users actually want it.
   - `What does "validated" mean here?` — You define what success looks like (signups, waitlist joins, click-through on a key feature, etc.) and the platform tracks it across your real-user sessions.
   - `When can I actually use it?` — We're in private beta. Joining the waitlist puts you in line for the next access wave.
8. **Final CTA** — Full-bleed dark section (`bg-ink-2`), beam line at top, centered h2 `Stop guessing. Start validating.`, sub `Join the waitlist to get early access.`, `WaitlistForm` again, same micro-disclaimer.
9. **Footer** — `border-t border-border`, `py-12`. Two columns on desktop / stacked on mobile. Left: wordmark + one-line `Built by Uncle Inc. © 2026.` Right: 3 column link list — `Product` (Features, Pricing, FAQ, Changelog), `Company` (About, Contact, Privacy, Terms), `Connect` (Twitter/X, LinkedIn — links point to `#` as honest placeholders with a `// TBD` mono suffix in dev only). Bottom hairline + `All rights reserved.` line.

## 4. USER FLOWS

This is a marketing site, so the primary "flow" is the waitlist capture. Supporting flows: in-page nav, FAQ toggling, mobile menu, and the pricing CTAs that all converge on the same waitlist form (single source of truth for the email, in a future build this posts to `/api/waitlist`).

### Flow A — Desktop primary: Landing → Waitlist join
1. User lands on `/`. Hero CTA is the email input (autofocused on desktop). User types email.
2. **Idle state:** Input shows `you@startup.com` placeholder, button reads `Join Waitlist`, button is `indigo` with subtle glow.
3. **Valid (typing) state:** Button enables, no inline error.
4. **Submit state (loading):** Button shows `Joining…` with a small spinner, input is disabled.
5. **Success state:** Form is replaced inline by a 2-line confirmation in teal: `You're on the list. We'll email you when the next access wave opens.` Input collapses, a small `// position #N` line appears in mono `text-muted` (N is a fake-but-plausible number, but in MVP we render `// position confirmed` to stay honest).
6. **Error state (network or invalid):** Button returns to idle, a 1-line red-tinted error appears under the input: `Something went wrong. Try again or email hello@uncle.inc.`
7. **Already-subscribed state:** Same success copy but with a softer tone: `You're already on the list. We'll be in touch.`

### Flow B — Mobile primary
Same as A, but the nav collapses to a hamburger, the hero stacks, and the waitlist input becomes full-width with the button below it. The form lives in the same component so behavior is identical.

### Flow C — FAQ toggle
1. User clicks a question. The `+` icon rotates 45° to `×` over 200ms.
2. The answer panel height animates from 0 to auto in 250ms ease-out.
3. Only one answer open at a time; opening one closes the others.

### Flow D — Mobile nav
1. Hamburger tap → full-screen overlay slides down from top, `bg-ink/95 backdrop-blur`.
2. Links stack at 32px line-height, mono uppercase, `text-2xl Space Grotesk`.
3. `Join Waitlist` button pinned to the bottom of the overlay.
4. Tap a link or the close `×` → overlay slides up, returns focus to the hamburger.

## 5. PAGES / ROUTES

| Route | Purpose | Layout / main elements |
|---|---|---|
| `/` | Single-page marketing site | All sections stacked: Nav → Hero → Honest strip → Features → How it works → Pricing → FAQ → Final CTA → Footer |
| `/api/waitlist` | POST endpoint for waitlist email capture | Accepts `{ email: string }`, validates with a simple regex, in MVP writes to a `waitlist.json` file or console logs (no real DB; honest `// storage TBD`). Returns `{ ok: true, position: null }`. |
| `/privacy` | Stub page | Same nav + footer, 1-paragraph honest placeholder: "Privacy policy coming soon. We do not sell your data. Email hello@uncle.inc with questions." |
| `/terms` | Stub page | Same as above with terms placeholder. |
| `/404` | Not found | Same nav + footer, centered h1 `Not found.` and a `Back to home` link. |

## 6. CORE FEATURES (on the marketing site)

1. **Waitlist capture form** — Email-only input, client-side regex (`/^[^\s@]+@[^\s@]+\.[^\s@]+$/`), POST to `/api/waitlist`, three states (idle / loading / success-or-error), single shared component used in Hero and Final CTA.
2. **Section navigation** — Sticky nav with anchor links (`#features`, `#pricing`, `#faq`) that smooth-scroll. Active section gets a 1px cyan underline that tracks scroll position via `IntersectionObserver`.
3. **FAQ accordion** — 5 questions, one open at a time, animated, keyboard-accessible (`aria-expanded`, `aria-controls`, focus-visible ring in cyan).
4. **Mobile menu** — Hamburger toggles full-screen overlay, body scroll locked while open, `Esc` key closes, focus trap inside overlay.
5. **Pricing comparison** — Static cards; the highlighted "Most popular" tier has a teal hairline border, a faint cyan `box-shadow` glow, and a small mono `// MOST POPULAR` tag at the top.
6. **How-it-works terminal preview** — Inline `<pre>`-style block in monospace with three example prompts and three generated next-step suggestions, presented as a preview, not a fake screenshot. Honest framing: `// EXAMPLE OUTPUT`.
7. **Beam-line motif** — A small `<BeamLine />` component (1px tall, 100% wide, gradient from `transparent` → `indigo` → `cyan` → `transparent`) used between sections and in the nav as the wordmark glyph.
8. **Honest "early access" framing** — No invented metrics, no fake testimonials. All scarcity/urgency comes from real facts: "We're in private beta", "Join the waitlist", "Early access opens to waitlist members first."

## 7. DATA MODEL

The marketing site is mostly static. The only mutable data is the waitlist. Since this is a pre-launch marketing site, the model is intentionally simple and honest — no fake "users" table, no fake activity feed.

```
WaitlistEntry
  id: string (nanoid, server-generated)
  email: string (validated, lowercased, unique)
  createdAt: ISO timestamp
  source: 'hero' | 'final-cta'  // which form they used
  referrer: string | null       // document.referrer, optional
```

If we later wire a real DB, we'd add `User`, `Project`, `Prototype`, `ValidationSession` — but planning those now would be invented scope. The site as specified has exactly one entity.

## 8. AUTH

**No auth on the marketing site.** The product goal is a marketing landing page; the validation platform itself (post-launch app) is out of scope for this build. When the actual product app is built later, auth will be email + password via Supabase Auth (or NextAuth Credentials provider) — no social OAuth buttons until real credentials are provisioned. No Clerk, ever.

## 9. FILES

```
package.json                  — Next 14, React 18, Tailwind, TypeScript, framer-motion, lucide-react, nanoid
next.config.js                — Minimal Next config, reactStrictMode true
tsconfig.json                 — Standard Next TS config
tailwind.config.ts            — Dark theme tokens, custom font families, content paths
postcss.config.js             — Tailwind + autoprefixer
.gitignore                    — node_modules, .next, .env*.local
app/layout.tsx                — Loads Space Grotesk + JetBrains Mono + Inter via next/font/google, sets dark bg
app/globals.css               — Tailwind directives, CSS vars (--ink, --indigo, --cyan, --teal), base resets
app/page.tsx                  — Imports and renders Nav, Hero, HonestStrip, Features, HowItWorks, Pricing, FAQ, FinalCTA, Footer
app/api/waitlist/route.ts     — POST handler, validates email, returns {ok}
app/privacy/page.tsx          — Stub privacy page
app/terms/page.tsx            — Stub terms page
app/not-found.tsx             — 404 page
components/Nav.tsx            — Sticky nav, wordmark + beam glyph, anchor links, waitlist CTA, mobile hamburger
components/BeamLine.tsx       — Reusable 1px gradient divider
components/WaitlistForm.tsx   — Shared form with idle/loading/success/error states, POSTs to /api/waitlist
components/Hero.tsx           — Eyebrow, h1, subhead, WaitlistForm, BeamLine
components/HonestStrip.tsx    — Single-line "currently in private beta" strip
components/Features.tsx       — Section header + 3x2 grid of FeatureCard
components/FeatureCard.tsx    — Index, icon, title, body, meta tag
components/HowItWorks.tsx     — 3 numbered steps with terminal preview block
components/TerminalPreview.tsx — Monospace preview block, // EXAMPLE OUTPUT header
components/Pricing.tsx        — Section header + 3 PricingCard
components/PricingCard.tsx    — Tier name, price, description, feature list, CTA button
components/FAQ.tsx            — Section header + 5 FAQItem
components/FAQItem.tsx        — Accordion row with aria attributes and animated reveal
components/FinalCTA.tsx       — Dark full-bleed section with WaitlistForm
components/Footer.tsx         — Wordmark, copyright, 3 link columns
lib/validators.ts             — email regex validator (shared between client and server)
lib/waitlist-store.ts         — In-memory append + append to data/waitlist.jsonl (dev only)
data/waitlist.jsonl           — Append-only log, gitignored except for .gitkeep
public/favicon.ico            — 32x32 ink-black square with cyan beam
```

## 10. ACCEPTANCE

A working build means:

- [ ] `npm install` and `npm run dev` start the site on `http://localhost:3000` with zero errors.
- [ ] `npm run build` succeeds with zero TypeScript errors.
- [ ] The page background is `#0a0a0f` (ink) everywhere; no white flashes on load.
- [ ] Headings render in Space Grotesk, body in Inter, code/labels in JetBrains Mono (verified in DevTools).
- [ ] The Hero h1 reads exactly `Validate Your Startup Idea Before You Build It.`
- [ ] The hero subhead mentions AI-assisted MVP validation for non-technical founders.
- [ ] The waitlist form in the Hero accepts an email, shows a loading state, and displays a teal success message on submit (or a red error on bad input).
- [ ] Submitting the form POSTs to `/api/waitlist` and the route returns `{ok: true}` for valid emails.
- [ ] The same `WaitlistForm` is reused in the Final CTA section and behaves identically.
- [ ] The Features section shows exactly 6 cards with the titles: AI Prototyping, Real User Testing, Launch Analytics, Guided Validation, Rapid Iteration, One-Click Deploy.
- [ ] The Pricing section shows exactly 3 tiers: Explorer ($0), Builder ($49/mo, highlighted), Team ($149/mo).
- [ ] The FAQ section has exactly 5 questions and uses a single-open accordion.
- [ ] No fake testimonials, no invented user counts, no fabricated revenue numbers, no invented press logos anywhere on the site.
- [ ] The site uses early-access / waitlist framing honestly ("private beta", "join the waitlist", "early access opens to waitlist members first").
- [ ] Sticky nav anchor links smooth-scroll to `#features`, `#pricing`, `#faq`.
- [ ] Mobile (≤768px): hamburger menu opens a full-screen overlay, hero stacks, pricing cards stack, form input becomes full-width.
- [ ] No external OAuth buttons (no "Sign in with Google/GitHub/Apple") on the marketing site.
- [ ] No Clerk dependency in `package.json`.
- [ ] `app/privacy/page.tsx` and `app/terms/page.tsx` render without errors.
- [ ] Beam-line motif is visible as a section divider in the Hero and as the wordmark glyph in the Nav.
- [ ] All Lucide icons use `strokeWidth={1.5}` for a consistent thin-line look.
- [ ] Section reveals animate on scroll (framer-motion `whileInView`), no parallax or scroll-jacking.
- [ ] The wordmark in Nav and Footer reads `Uncle` with a `.` in cyan.
- [ ] Copyright in Footer reads `© 2026 Uncle Inc.`

FILES: ["package.json","next.config.js","tsconfig.json","tailwind.config.ts","postcss.config.js",".gitignore","app/layout.tsx","app/globals.css","app/page.tsx","app/api/waitlist/route.ts","app/privacy/page.tsx","app/terms/page.tsx","app/not-found.tsx","components/Nav.tsx","components/BeamLine.tsx","components/WaitlistForm.tsx","components/Hero.tsx","components/HonestStrip.tsx","components/Features.tsx","components/FeatureCard.tsx","components/HowItWorks.tsx","components/TerminalPreview.tsx","components/Pricing.tsx","components/PricingCard.tsx","components/FAQ.tsx","components/FAQItem.tsx","components/FinalCTA.tsx","components/Footer.tsx","lib/validators.ts","lib/waitlist-store.ts","data/.gitkeep","public/favicon.ico"]