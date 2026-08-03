<h1 align="center">Bicktivism Z</h1>

<p align="center">
  Security researcher. I find and report vulnerabilities in software people actually run — web2 and web3.
</p>

<p align="center">
  <a href="https://github.com/guzzle/guzzle/security/advisories/GHSA-v5mv-p594-2x33"><img alt="guzzlehttp/guzzle — High, CVSS 7.2" src="https://img.shields.io/badge/guzzlehttp%2Fguzzle-High%20%C2%B7%20CVSS%207.2-c0392b?style=flat-square"></a>
  <a href="https://github.com/aio-libs/yarl/releases/tag/v1.24.5"><img alt="aio-libs/yarl — Medium, patched in 1.24.5" src="https://img.shields.io/badge/aio--libs%2Fyarl-Medium%20%C2%B7%20patched%201.24.5-e67e22?style=flat-square"></a>
  <a href="#published-advisories"><img alt="credited reporter" src="https://img.shields.io/badge/credited-reporter-2c7a4b?style=flat-square"></a>
  <a href="#support-the-work"><img alt="Buy me a coffee" src="https://img.shields.io/badge/buy%20me%20a%20coffee-EVM-FFDD00?style=flat-square&logo=ethereum&logoColor=black"></a>
</p>

<p align="center"><em>Every claim on this page links to something you can open.</em></p>

---

### Published advisories

**[GHSA-v5mv-p594-2x33](https://github.com/guzzle/guzzle/security/advisories/GHSA-v5mv-p594-2x33)** — *Noncanonical host can bypass host-based checks in `guzzlehttp/guzzle`*

- **High — CVSS 3.1 score 7.2** (`AV:N/AC:L/PR:N/UI:N/S:C/C:L/I:L/A:N`)
- Affects `< 7.15.2` and `>= 8.0.0, < 8.0.1` · patched in **7.15.2** and **8.0.1**
- Published 2026-07-26 · credited reporter

**GHSA-859q-jpx8-p5mm** — *yarl silently strips default-ignorable code points from the host*

- **Medium** — CWE-436 (Interpretation Conflict) + CWE-918 (SSRF)
- Affects `yarl <= 1.24.2` · patched in **[1.24.5](https://github.com/aio-libs/yarl/releases/tag/v1.24.5)**
- Fix: [aio-libs/yarl#1801](https://github.com/aio-libs/yarl/pull/1801) — *"Reject hosts with Unicode default-ignorable code points"*
- Accepted; advisory pending publication, so the release and the patch commit are the public record

---

### The common thread

Both findings are the same bug class in two different language ecosystems, found by the same method:
**a URL library and the code that validates it disagree about what the host is.** The validator
inspects one host string; the client then connects somewhere else. Guzzle is PHP, yarl is Python —
the class does not care about the language.

That is the work: pick a transformation that runs before a security decision, measure what it
actually does to its whole input space instead of guessing, and then look for a consumer that
re-derives the value differently.

---

### How I work

- **Nothing is reported until it has been executed.** A conclusion from reading source is a
  hypothesis. It stays a hypothesis until a test drives the real code and fails without the bug.
- **Every negative result needs a positive control.** If a search returns nothing, I first prove
  the search can return something.
- **The impact ladder gets climbed all the way**, and where a rung does not hold, the report says so.

Active in web3 audit contests and bug bounty programs alongside the open-source work.

---

### Support the work

Findings like the ones above take weeks of unpaid execution — building the lab, running the controls,
and writing the negative results down as carefully as the positive ones. If any of it saved you time,
a coffee is genuinely appreciated.

**EVM address** — Ethereum and EVM-compatible chains:

```
0x5A1d2EFAeef4cd4c8C4F9d8D78B10fbE8b22B814
```

No obligation, and it changes nothing about what gets reported or to whom.

---

<p align="center">📫 <code>admin@researchcti.cyou</code></p>
