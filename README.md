# Grand Slam Offer Architect — Claude Skill

A self-contained Claude skill that acts as a senior offer-building consultant.
It guides a user through an **11-part process** to build or strengthen a specific
**Grand Slam Offer** and produce a **One-Page Offer Doc** for their Landing Page,
ads, and sales calls — for any business type.

It combines two frameworks:
- **Alex Hormozi's *$100M Offers*** — Value Equation, market selection, premium
  pricing, the Problems→Solutions→Delivery→Trim & Stack process, and the four
  enhancers (Scarcity, Urgency, Bonuses, Guarantees) + M-A-G-I-C naming.
- **7 Days Sales Funnels Offer Building** — Buyer Qualifiers, Dream Outcome,
  Obstacle Inventory, Solution Map, Delivery Vehicles, Proof Plan, Funnel Offer
  Stack (AOV), and the Hook-Story-Offer script.

## Structure

```
grand-slam-offer-architect/
├── SKILL.md                         # Entry point: identity, rules, the 11-part
│                                    #   workflow, quality gate, final output,
│                                    #   edge cases, and the reference map.
├── references/                      # Deep framework theory, loaded on demand
│   ├── value-equation.md            #   The 4 value drivers, in depth
│   ├── buyer-and-market.md          #   Lost-Chapter avatar method + market indicators
│   ├── market-and-pricing.md        #   Commodity problem, growth levers, premium pricing
│   ├── offer-creation.md            #   The 5-step create process + Delivery Cube + Trim & Stack
│   ├── offer-enhancers.md           #   Scarcity, Urgency, Bonuses, Guarantees, M-A-G-I-C naming
│   ├── glossary.md                  #   Every key term defined
│   └── source-texts/                # Source of truth (searchable, page-mapped)
│       ├── 100M-Offers-full.txt         #   Full book text (205 pp)
│       ├── 100M-Offers-Lost-Chapter.txt #   The Lost Chapter (8 pp)
│       ├── GPT-Instructions.txt         #   Original Custom GPT instructions (14 pp)
│       ├── extraction-manifest.json     #   Page counts + SHA-256 hashes
│       ├── 100M Offers Alex Hormozi.pdf
│       ├── 100M Offers The Lost Chapter Alex Hormozi_compressed.pdf
│       └── 1AR Grand Slam Offer Architect Custom GPT Instructions.pdf
└── assets/
    ├── one-page-offer-doc-template.md   # Fillable final-output template
    └── worked-example-offer-doc.md      # A complete filled example (physio clinic)
```

## How it was built

The workflow spine is derived from the **Custom GPT Instructions** (the source of
truth for behavior). The `references/` files distill the **full frameworks** from
*$100M Offers* and its Lost Chapter so the skill's questions, examples, and audits
are grounded in the real methodology — nothing helpful from the source PDFs is
left out. The original PDFs and their page-mapped text extractions are preserved
under `references/source-texts/` for verification and deep dives.

## Install (Claude Code)

Copy the whole folder into your skills directory, then restart Claude Code:

```bash
# personal (all projects)
cp -r "grand-slam-offer-architect" ~/.claude/skills/

# or project-scoped
mkdir -p .claude/skills && cp -r "grand-slam-offer-architect" .claude/skills/
```

Claude reads `SKILL.md`'s front-matter `description` to decide when to invoke the
skill, and loads the `references/` and `assets/` files as needed while running the
workflow. You can also invoke it explicitly (e.g. `/grand-slam-offer-architect`)
where slash-invocation is supported.

## Language

Defaults to the user's language: **English** unless the user writes in Arabic or
asks for Arabic, in which case it responds in **White Arabic with English technical
terms** (the term list is fixed in `SKILL.md` and `references/glossary.md`).

## Guardrails

Never fabricates proof, testimonials, results, market facts, or guarantees. The
frameworks are tools; the facts always come from the user's real business (or, for
theory, from the source texts).
