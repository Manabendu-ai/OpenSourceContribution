# 🌱 Open Source Contributions

A running log of every open source contribution I make — what I fixed, why it mattered, and what I learned along the way.

<p align="center">
  <img src="https://img.shields.io/badge/Contributions-1-brightgreen?style=for-the-badge" alt="Contributions"/>
  <img src="https://img.shields.io/badge/Status-Active-blue?style=for-the-badge" alt="Status"/>
  <img src="https://img.shields.io/badge/First%20PR-2026-orange?style=for-the-badge" alt="First PR"/>
</p>

---

## 📌 Why this repo exists

I'm documenting my open source journey — one contribution at a time. Each entry below captures the repo, the issue, what I actually changed, and the key things I learned. This isn't just a changelog; it's proof of work and a personal record of growth.

> 💡 **Format for each entry:** Repo → Issue/PR → What I did → Key takeaways

---

## 📋 Contributions Log

### 1. [sklearn-genetic-opt](https://github.com/rodrigo-arenas/Sklearn-genetic-opt)

| | |
|---|---|
| **Type** | 🧪 Test Coverage |
| **Issue** | [#258 – Make `_candidate_label` tests cover long labels and hidden parameters](https://github.com/rodrigo-arenas/Sklearn-genetic-opt/issues/258) |
| **Pull Request** | [#307 – Add tests for `_candidate_label`](https://github.com/rodrigo-arenas/Sklearn-genetic-opt/pull/307) |
| **Status** | ✅ Merged |
| **Stack** | Python, pytest, scikit-learn |

**What it was about:**
`sklearn-genetic-opt` is a scikit-learn-compatible hyperparameter tuning library that uses genetic algorithms instead of grid/random search. It has a private helper, `_candidate_label`, used internally by its plotting functions to generate short, readable labels for GA candidates (e.g. `max_depth=5, n_estimators=100, +2 more`). This helper had no dedicated unit tests.

**What I did:**
Added 4 focused unit tests directly targeting `_candidate_label` in `test_plots.py`, following the existing test conventions in the repo (no fixtures needed, plain dict inputs, matching the style of the `_as_list` tests already present).

**🔑 Key points:**

- ✅ **Hidden parameter count** — verified that when a candidate has more parameters than `max_label_params`, the label correctly appends `+N more`.
- ✅ **Explicit `label_params` filter** — confirmed that passing a specific list of parameter names restricts the label to *only* those keys, with no "more" suffix.
- ✅ **Truncation behavior** — tested that labels exceeding `max_length` are cut and suffixed with `...`, and the final string respects the exact length limit.
- ✅ **Float formatting** — validated that `float_precision` correctly formats numeric values (e.g. `0.123456789` → `0.123`) using the existing compact formatting logic.
- ✅ Zero changes to production code (`plots.py`) — pure test-only PR, per the issue's explicit guidance to avoid touching plotting behavior unless a real bug was found.

**💡 What I learned:**
- How to navigate a real, unfamiliar codebase — tracing a function from a GitHub issue to its actual implementation using `grep`.
- The importance of matching a project's existing test style/conventions rather than imposing your own.
- Git hygiene basics the hard way — staged changes ≠ committed changes! (Learned to always double-check `git log` before pushing.)
- The full open source contribution lifecycle end-to-end: fork → clone → branch → implement → test → format (`black`) → commit → push → PR → review → merge.

---

## 🚀 Coming up

More contributions will be added here as they happen. Stay tuned.

---

<p align="center">
  <sub>Maintained with ☕ and a lot of <code>git status</code> checks.</sub>
</p>