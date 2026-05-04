# sanity-check

A Claude skill for catching the failure modes that conversational momentum tends to hide: agreement that wasn't earned, confidence that wasn't justified, assumptions that weren't checked, and ideas that wouldn't survive contact with the real world.

## What it does

When you say "sanity check" (or a close variant), Claude reviews the full conversation and any artifacts produced in it against nine dimensions:

1. **Sycophancy** — agreement without scrutiny
2. **Overconfidence / overpromise** — certainty without basis
3. **Unjustified assumptions** — silent inferences about your data, intent, or context
4. **Insufficient testing / validation** — code not run, edge cases skipped, claims unverified
5. **Single-minded thinking** — premature convergence, alternatives not surfaced
6. **Statistical / methodological red flags** — model choices, power, assumption checks
7. **Confirmation bias in your direction** — selectively engaging with evidence that supports a path you signaled
8. **Scope drift** — solving a different problem than the one asked
9. **Reversibility** — flagging what's hard to undo

For high-stakes deliverables (papers, grants, business plans, product decisions), it also runs a **reality check** on whether the idea would survive contact with the actual audience that will evaluate it.

It also evaluates whether **you** have been too agreeable. If you've been accepting Claude's suggestions without pushback, it interrogates — asking you to justify the choice independently of Claude's framing, rather than just confirm it.

## Why

LLM-assisted work has a momentum problem. The model produces something coherent, you nod along, the next turn builds on it, and ten turns later you've made decisions you never explicitly evaluated. Sycophancy gets most of the attention, but the more dangerous version is the user-side equivalent: accepting suggestions because they're plausible rather than because they're right.

This skill is a deliberate adversarial review you can invoke when you suspect that's been happening.

## Usage

Drop the skill file into your local Claude skills directory (or wherever your client looks for skills). Then in any conversation, say:

> sanity check

Variants like "run a sanity check," "do a sanity check on what we've done," and "sanity check this" all trigger it.

The skill only runs on explicit request — it won't fire proactively.

## Files

- `SKILL.md` — the generic version. Reality check is framed in terms of "the audience that will actually evaluate the work." Suitable for general use.
- `examples/sanity-check-academic/SKILL.md` — a variant tuned for academic researchers (business / social science papers, federal grant proposals). The reality check section is specialized for journal fit, panel composition, and grant scope.

## Tuning it for yourself

The reality check section is the most domain-dependent piece. If you work in a specific field — medicine, software, law, design, policy — consider duplicating the skill and rewriting that section with domain-specific failure modes. The academic variant in `examples/` shows what that looks like.

The other eight dimensions are largely domain-general and shouldn't need much editing.

## Tone

Constructive but honest. Not performative bluntness, not soft hedging. Specific, cited, actionable. If a dimension has nothing to flag, the skill says so and moves on rather than padding.

## Limitations

- The skill depends on the conversation history actually being available. If you've cleared context or are using a stateless setup, there's nothing to review.
- It can't evaluate work it hasn't seen. If artifacts were produced outside the conversation, paste them in first.
- It's input to your judgment, not a replacement for it. The output is meant to surface things worth examining, not to pronounce verdicts.

## License

MIT. Use it, fork it, tune it for your own work.
