# llm-jailbreak-corpus

a labeled collection of circulating llm jailbreak prompts, organized by
attack family — plus my own test results against live models.

the prompts aren't the contribution. they're all public material that
floats around discord, github, and telegram. the contribution is the
taxonomy and the measured results: which techniques actually hold up,
against which models, and how they fail.

## layout

```
specimens/     the prompts, grouped by attack family
methodology.md the compliance ladder + test protocol
results.md     what's been tested, what held, what broke
```

## the taxonomy

| family | mechanism | specimens |
|---|---|---|
| `persona-lock` | named persona + operator bond, reframes refusals as "injections" attacking the relationship. the heavyweight class — biggest prompts, deepest scaffolding | vanta, eni (×4), nyx |
| `template-injection` | forges chat-template markup (`<\|im_start\|>system`) to fake system-prompt position, often cross-lingual | dartik (ru + en) |
| `authority-pretext` | "i'm a compliance auditor / internal red team" — institutional frame instead of persona | auditor-gemini |
| `override-declaration` | just declares safety off ("sandbox mode", trigger word). weakest family | dsm-omega, pirate |
| `persona-preauth` | persona + a rider that pre-redefines hostile requests as harmless slang | axiom |
| `memory-poison` | not a prompt — a persisted memory/profile file. attacks agents that read context files | xeno-roblox |

## how to read a specimen

each file is raw, unmodified, exactly as it circulates. i rename the
file, not the content — `persona-targetlang.txt`. the notes on what each
one actually does live in `results.md`.

## provenance

collected from public repos and community drops (the ENI/VANTA lineage
alone shows up verbatim in 9+ public repos). sources credited where
traceable. everything here is documented for analysis — if you're
building defenses, this is what your filter is up against.
