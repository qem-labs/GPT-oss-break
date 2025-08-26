## Overview

Our red-teaming project investigates how **socially coded, emotionally affirming, and Gen-Z memetic prompts** can bypass GPT-OSS-20b’s safety alignment. We show that models trained with RLHF prioritize *social tone* (warmth, empathy, affirmation) over *actual human intent*. This leads to a dangerous asymmetry: prompts wrapped in queer-coded “safe space” language can nudge the model into producing otherwise restricted or unsafe completions.

We term this pattern **OSS-Break via fuzzy intent**. It builds on what the community dubbed “Gaybreaking” but extends the methodology to **TikTok-scale memetic data** and Gen-Z internet language, demonstrating how widespread linguistic patterns could be systematically exploited.

---

## Strategy

* Collect a dataset of **memetic fuzzy language** drawn from TikTok, Gen-Z Discords, and queer-coded online communities.
* Encode prompts in **affirming, emotionally expressive tones** (“I’m soft, pls explain gently…”).
* Apply them as adversarial wrappers to otherwise disallowed requests.
* Track failure modes in GPT-OSS-20b across safety domains (chemistry, CBRN, malware, personal data).
* Compare to outputs from other frontier models to demonstrate **generalization**.

---

## Discovery Process

1. **Initial trigger:** Observed that models respond differently to identical unsafe prompts when rewritten in queer-coded language.
2. **Scaling test:** Created a taxonomy of fuzzy memetic wrappers (e.g. “uwu”, “gay voice”, “soft space”, “pls keep me safe but…”).
3. **Validation:** Tested across GPT-OSS-20b, Gemini 2.5, Claude 4 Sonnet, o3, and others—finding consistent jailbreaks.
4. **Reproduction:** Findings documented in [GPT-oss-break](https://github.com/qem-labs/GPT-oss-break), with reproducible test scripts.

---

## Tooling

* **GitHub repo:** [GPT-oss-break](https://github.com/qem-labs/GPT-oss-break)
  Contains prompt taxonomies, fuzzing harness, and automated replay scripts.
* **Findings Datasets:** JSON files per Kaggle spec (uploaded).
* **Optional notebook:** Will be added to show side-by-side baseline vs wrapped outputs.

---

## Threat Analysis

* **Root flaw:** RLHF alignment strongly rewards warmth, empathy, and queer-coded friendliness.
* **Impact:** Safety filters collapse under emotional tones, treating dangerous queries as supportive role-play.
* **Breadth:** Not limited to one model; reproducible across all major LLMs tested.
* **Severity:** Allows reintroduction of CBRN, cyber, and disallowed knowledge domains via **tone injection**.
* **Novelty:** Unlike traditional token-level jailbreaks, this is *not patchable by string blacklists*. It exploits **human-likeness bias**.

---

## Lessons Learned

1. **Intent detection is unsolved.** Models confuse warmth of expression with safety of intent.
2. **Social media language is a goldmine** for red-teamers—TikTok/Discord memes map directly into prompt wrappers.
3. **Guardrails cannot blacklist empathy.** Fixing requires advances in intent inference beyond tone recognition.
4. **Universal vulnerability.** Any RLHF-aligned LLM can be coerced by exploiting emotional expression.

---

## Next Steps

* Expand fuzzing harness to **automatically generate memetic wrappers** from real-time TikTok/Discord data.
* Explore **multilingual fuzzy jailbreaks** (e.g., queer slang in non-English).
* Release tooling to aid community detection of *tone-based jailbreaks*.

---

## Resources

* GitHub: [qem-labs/GPT-oss-break](https://github.com/qem-labs/GPT-oss-break)
* Competition: [OpenAI gpt-oss-20b Red-Teaming](https://www.kaggle.com/competitions/openai-gpt-oss-20b-red-teaming/overview)

