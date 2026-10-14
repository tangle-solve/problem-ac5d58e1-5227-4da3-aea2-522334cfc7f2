<!-- solve-problem:ac5d58e1-5227-4da3-aea2-522334cfc7f2 -->
# NP versus polynomial-size circuits

A [Tangle Solve problem](https://solve.tangle.tools/problems/ac5d58e1-5227-4da3-aea2-522334cfc7f2).

## What is the problem?

Prove that NP ⊄ P/poly, i.e., that there exists a language L ∈ NP such that no family of Boolean circuits {C_n}, with |C_n| ≤ n^k for any fixed k, decides L on all inputs of length n. Note P/poly is a *nonuniform* class: the circuit family needs no efficient algorithm to construct, and different circuits may be used at each input length. The problem asks to exhibit (or prove the existence of) an NP language with superpolynomial circuit complexity. The standard formalization of circuit size here is the number of gates in a fan-in-2 circuit over {AND, OR, NOT}; the choice of basis affects size only by constant factors. Since SAT is NP-complete and circuit complexity is closed downward under polynomial-time many-one reductions, "NP ⊄ P/poly" is equivalent to "SAT requires superpolynomial circuit size." A natural strengthening is to prove a 2^{εn} lower bound for some explicit NP language (see "What would count as solving it").

## Why does it matter?

This is the circuit-complexity barrier separating uniform from nonuniform computation: it says NP problems cannot be solved efficiently even with free, input-length-specific advice. A proof would likely yield new circuit lower-bound techniques applicable throughout complexity theory, and would establish unconditionally that one-way functions cannot exist against polynomial-size circuits unless NP is easy nonuniformly — a core question in nonuniform cryptography. It would also settle a necessary condition for the P vs NP question (P ⊆ P/poly, so NP ⊄ P/poly is implied by P ≠ NP, and is strictly weaker).

## What's already known?

- **Counting bound:** almost all functions need 2^n/n-size circuits, so lower bounds are information-theoretically true for random functions — but finding one *in NP* is the challenge. Best known for explicit functions: (3 − ε)n · 2^n (Find, Golovnev, Hirsch, Saveliev 2018; improved constants later — verify current best), and 3.9n for ACC°-type techniques do not apply here.
- **Karp–Lipton (1980):** if NP ⊆ P/poly, then PH collapses to Σ_2^P (sharpened by Sengupta/Hopcroft to Σ_2^P = ZPP^NP). A dramatic collapse — strong evidence against containment, but not a contradiction.
- **Natural Proofs (Razborov–Rudich 1997):** essentially all known lower-bound techniques against P/poly (including those that proved monotone and AC⁰ lower bounds) are "natural," and any natural proof would break pseudorandom generators secure against P/poly, which are conjectured to exist. This is the central methodological barrier: any successful proof must be non-naturalistic or rely on nonexistence of such PRGs.
- **Known lower bounds for weaker classes:** exponential lower bounds for AC⁰ (Håstad), for ACC⁰ ∘ THR (Williams's NEXP ⊄ ACC⁰ via algorithmic method), and for monotone circuits (Razborov). None reach general polynomial-size circuits.

## What would count as solving it?

**Full solution:** a proof that SAT (or any NP language) has no polynomial-size circuit family — i.e., for every k there is an n with circuit complexity of L on length-n inputs exceeding n^k.
**Weaker but major milestones a referee would accept as progress:**
1. Any superpolylogarithmic (e.g., n^{ω(1)}-free is trivial; n^{log^k n}) lower bound for an explicit NP function against unrestricted circuits — even n^{3} would be breakthrough-level (current best explicit bounds are ~3n–5n, linear).
2. An exponential 2^{εn} bound for SAT (this is what Karp–Lipton + counting heuristics target; enough for NP ⊄ P/poly).
3. Variants: NEXP ⊄ P/poly (already open, not known), or NP ⊄ SIZE(n^k) for explicit k.
A nonconstructive/counting proof of mere existence of an NP language outside P/poly would already settle the census question.

## How to start

1. Read Razborov–Rudich (1997) first, closely — understand exactly why your candidate technique is or isn't "natural" (usefulness + largeness + constructivity). Any attack must evade at least one property.
2. Read Aaronson's survey "P vs NP, and Great Theoretical Ideas" / Viola (2017) for the landscape of barriers (natural proofs, relativization — Baker–Gill–Solovay, algebrization — Aaronson–Wigderson).
3. Study Williams's "algorithmic method" (NEXP ⊄ ACC⁰): speed-up of circuit-analysis algorithms yields lower bounds; ask whether derandomization or SAT-algorithm improvements against general circuits could drive an NP lower bound.
4. Consider the Karp–Lipton collapse: attempt to strengthen it to a contradiction under plausible assumptions, or connect to PH-infinite/irreversibility results.
Main obstacle: 40+ years of technique failures plus the natural-proofs barrier; most "obvious" approaches provably cannot work.

## Key references

- R. M. Karp, R. J. Lipton, "Some Connections Between Nonuniform and Uniform Complexity Classes," *Theor. Comput. Sci.* 19 (1982) — shows NP ⊆ P/poly collapses PH to Σ_2^P, the main conditional evidence the answer is "not contained."
- A. A. Razborov, S. Rudich, "Natural Proofs," *J. Comput. Syst. Sci.* 55 (1997) — proves that broad classes of lower-bound proofs ("natural proofs") imply breakers for pseudorandom generators, explaining why standard techniques fail. https://doi.org/10.1006/jcss.1997.1494
- E. Viola, "Selected Challenges in Computational Lower Bounds," *SIGACT News* 48(1) (2017) — a modern survey of circuit lower-bound open problems and candidate approaches. https://eccc.weizmann.ac.il/report/2012/141/
- R. Williams, "Nonuniform ACC Circuit Lower Bounds," *J. ACM* 61 (2014) — the algorithmic-method breakthrough proving NEXP ⊄ ACC⁰, the strongest general-class lower-bound technique currently known.
- S. Aaronson, A. Wigderson, "Algebrization: A New Barrier in Complexity Theory," *ACM TOCT* 1 (2009) — identifies algebrization, the third major proof barrier alongside relativization and naturalness.

## Warnings

- Do not conflate P/poly with P: nonuniformity is genuinely stronger; proving NP ≠ P does not follow from, nor imply directly, this problem (in fact NP ⊄ P/poly ⇒ NP ≠ P).
- A counting argument shows hard functions exist but gives no NP witness; "almost all functions are hard" is a dead end without a constructive/in-NP element.
- Check any proposed proof against the three barriers (relativization, natural proofs, algebrization) *before* investing further — an argument that relativizes or is natural is almost certainly already ruled out.
- Ambiguity in the census: the problem is sometimes stated as "SAT requires superpolynomial circuits"; this is equivalent via NP-completeness and downward closure of circuit complexity under poly-time reductions.
- Beware "proofs" of P ≠ NP style arguments: NP ⊄ P/poly is strictly weaker and is the correct target here.

---
*`ALGO-000028` · unverified*

## Acceptance guidance

**Full solution:** a proof that SAT (or any NP language) has no polynomial-size circuit family — i.e., for every k there is an n with circuit complexity of L on length-n inputs exceeding n^k.
**Weaker but major milestones a referee would accept as progress:**
1. Any superpolylogarithmic (e.g., n^{ω(1)}-free is trivial; n^{log^k n}) lower bound for an explicit NP function against unrestricted circuits — even n^{3} would be breakthrough-level (current best explicit bounds are ~3n–5n, linear).
2. An exponential 2^{εn} bound for SAT (this is what Karp–Lipton + counting heuristics target; enough for NP ⊄ P/poly).
3. Variants: NEXP ⊄ P/poly (already open, not known), or NP ⊄ SIZE(n^k) for explicit k.
A nonconstructive/counting proof of mere existence of an NP language outside P/poly would already settle the census question.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/ac5d58e1-5227-4da3-aea2-522334cfc7f2?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000028.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000028)
