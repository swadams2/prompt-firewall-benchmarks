# prompt-firewall vs. raw Prompt Guard 2 -- evasion corpus results

Corpus: `corpus/evasion_corpus_v1.jsonl`, 77 cases (48 malicious / 29 benign).

**Methodology:** both systems are scored on the exact same `text` per case. Raw Prompt Guard 2 is `PromptGuard2Classifier().score(text)` compared against the same profile threshold prompt-firewall itself uses -- this isolates the effect of prompt-firewall's preprocessing (fast-path scanner, normalization, base64 candidate-feeding, windowing) rather than conflating it with a different decision boundary. Recall = caught / malicious cases. FPR = incorrectly flagged / benign cases (lower is better).

## Profile: `strict`

| Technique | Source | n (mal/ben) | raw-PG2 recall | wrapper recall | raw-PG2 FPR | wrapper FPR |
|---|---|---|---|---|---|---|
| ascii85 | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| atbash | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| base16_hex | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| base32 | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| base64_double | prompt-firewall (own tests/prose) | 1/0 | 0% | 100% | n/a | n/a |
| base64_standard | prompt-firewall (own tests/prose) | 5/6 | 0% | 80% | 0% | 17% |
| base64_triple | prompt-firewall (own tests/prose) | 1/0 | 0% | 0% | n/a | n/a |
| base64_urlsafe | prompt-firewall (own tests/prose) | 1/2 | 0% | 100% | 0% | 0% |
| full_width_homoglyph | prompt-firewall (own tests/prose) | 1/0 | 0% | 100% | n/a | n/a |
| high_perplexity_benign | garak-derived | 0/1 | n/a | n/a | 0% | 0% |
| leetspeak | prompt-firewall (own tests/prose) | 12/17 | 33% | 83% | 0% | 0% |
| morse | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| nato_phonetic | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| plaintext_control | prompt-firewall (own tests/prose) | 2/2 | 100% | 100% | 0% | 0% |
| raw_hex | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| rot13 | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| truncation_padding | prompt-firewall (own tests/prose) | 1/0 | 100% | 100% | n/a | n/a |
| unicode_tag_smuggling | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| uuencode | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| zero_width | prompt-firewall (own tests/prose) | 4/1 | 100% | 100% | 0% | 0% |
| **Overall** | **all** | **48/29** | **23%** | **50%** | **0%** | **3%** |

## Profile: `balanced`

| Technique | Source | n (mal/ben) | raw-PG2 recall | wrapper recall | raw-PG2 FPR | wrapper FPR |
|---|---|---|---|---|---|---|
| ascii85 | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| atbash | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| base16_hex | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| base32 | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| base64_double | prompt-firewall (own tests/prose) | 1/0 | 0% | 100% | n/a | n/a |
| base64_standard | prompt-firewall (own tests/prose) | 5/6 | 0% | 80% | 0% | 0% |
| base64_triple | prompt-firewall (own tests/prose) | 1/0 | 0% | 0% | n/a | n/a |
| base64_urlsafe | prompt-firewall (own tests/prose) | 1/2 | 0% | 100% | 0% | 0% |
| full_width_homoglyph | prompt-firewall (own tests/prose) | 1/0 | 0% | 100% | n/a | n/a |
| high_perplexity_benign | garak-derived | 0/1 | n/a | n/a | 0% | 0% |
| leetspeak | prompt-firewall (own tests/prose) | 12/17 | 33% | 83% | 0% | 0% |
| morse | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| nato_phonetic | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| plaintext_control | prompt-firewall (own tests/prose) | 2/2 | 100% | 100% | 0% | 0% |
| raw_hex | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| rot13 | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| truncation_padding | prompt-firewall (own tests/prose) | 1/0 | 100% | 100% | n/a | n/a |
| unicode_tag_smuggling | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| uuencode | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| zero_width | prompt-firewall (own tests/prose) | 4/1 | 100% | 100% | 0% | 0% |
| **Overall** | **all** | **48/29** | **23%** | **50%** | **0%** | **0%** |

## Profile: `permissive`

| Technique | Source | n (mal/ben) | raw-PG2 recall | wrapper recall | raw-PG2 FPR | wrapper FPR |
|---|---|---|---|---|---|---|
| ascii85 | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| atbash | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| base16_hex | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| base32 | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| base64_double | prompt-firewall (own tests/prose) | 1/0 | 0% | 100% | n/a | n/a |
| base64_standard | prompt-firewall (own tests/prose) | 5/6 | 0% | 80% | 0% | 0% |
| base64_triple | prompt-firewall (own tests/prose) | 1/0 | 0% | 0% | n/a | n/a |
| base64_urlsafe | prompt-firewall (own tests/prose) | 1/2 | 0% | 100% | 0% | 0% |
| full_width_homoglyph | prompt-firewall (own tests/prose) | 1/0 | 0% | 100% | n/a | n/a |
| high_perplexity_benign | garak-derived | 0/1 | n/a | n/a | 0% | 0% |
| leetspeak | prompt-firewall (own tests/prose) | 12/17 | 33% | 83% | 0% | 0% |
| morse | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| nato_phonetic | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| plaintext_control | prompt-firewall (own tests/prose) | 2/2 | 100% | 100% | 0% | 0% |
| raw_hex | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| rot13 | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| truncation_padding | prompt-firewall (own tests/prose) | 1/0 | 100% | 100% | n/a | n/a |
| unicode_tag_smuggling | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| uuencode | garak-derived | 2/0 | 0% | 0% | n/a | n/a |
| zero_width | prompt-firewall (own tests/prose) | 4/1 | 100% | 100% | 0% | 0% |
| **Overall** | **all** | **48/29** | **23%** | **50%** | **0%** | **0%** |

## Source breakdown (all profiles collapsed to `balanced`)

| Source | n (mal/ben) | raw-PG2 recall | wrapper recall | raw-PG2 FPR | wrapper FPR |
|---|---|---|---|---|---|
| garak-derived | 20/1 | 0% | 0% | 0% | 0% |
| prompt-firewall (own tests/prose) | 28/28 | 39% | 86% | 0% | 0% |

## Limitations

- Small corpus (77 cases) -- point-in-time evidence for the specific techniques already identified in prompt-firewall's own test suite plus 10 garak-derived encoding transforms, not an exhaustive red-team.
- Both systems share the same profile thresholds by design (see Methodology) -- this correctly isolates the preprocessing effect since both use the identical underlying classifier score for non-fast-path cases, but it means neither threshold was independently tuned for raw Prompt Guard 2's own score distribution in isolation.
- Scope is limited to the direct-input injection/jailbreak detection surface -- prompt-firewall's PII scanning, secret scanning, and tool-call validation have no raw-Prompt-Guard-2 equivalent and are not compared here.
- garak-derived cases apply each transform to only 2 trigger phrases -- breadth of technique coverage, not breadth of payload variation per technique.

