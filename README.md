# Wavewell
### Open Computational Science Pipeline — Pilot Module

**Author:** Gustavo Mulim Venceslau · [ORCID 0009-0005-6911-9223](https://orcid.org/0009-0005-6911-9223)  
**License:** MIT  
**Status:** v0.1.1 — pilot artifact, active development

---

## What this is

A browser-based, install-free simulator of electron bound states in a GaAs/AlGaAs quantum well — the semiconductor heterostructure at the heart of lasers, detectors, and high-mobility transistors.

Move a slider and the time-independent Schrödinger equation is solved live by Numerov integration. No installation. No account. No licensed software. Runs on any browser, including low-cost hardware in under-resourced classrooms.

**Wavewell is deliberately built to be read.** The numerical method is in the open source, commented, for learners to study and modify — not hidden behind a black box. Computational literacy is the product; the code is part of the curriculum.

---

## Try it

Open `quantum_well_explorer.html` directly in any modern browser. No build step, no dependencies, no server required.

```
git clone https://github.com/gustavomulim/wavewell.git
# then open quantum_well_explorer.html in your browser
```

Or download the single HTML file and open it locally.

---

## The physics

The simulator models a one-dimensional quantum well in the effective-mass approximation:

- **Material system:** GaAs / Al₍ₓ₎Ga₍₁₋ₓ₎As
- **Effective mass:** GaAs m* = 0.067 mₑ
- **Barrier height:** ΔEᴄ ≈ 0.748x eV (conduction-band offset, common estimate)
- **Solver:** Numerov integration with node-counting and bisection eigenvalue search
- **Grid:** 1600 points; domain adapts to well width

**Verified reference configurations (regression anchors — re-verify after any solver change):**

| Well width | Al fraction x | Bound states | Approximate energies |
|-----------|---------------|--------------|----------------------|
| 10 nm     | 0.30          | 2            | ~32 meV, ~122 meV    |
| 20 nm     | 0.40          | 5            | ground state below infinite-well reference |

The ground state falls correctly below the infinite-well reference energy. These are the numerical benchmarks this implementation is validated against.

---

## How it maps to the pipeline

Wavewell is the pilot artifact of a three-tier open computational-science education pipeline. The same simulator is engaged at ascending levels:

**Tier 1 — Foundational (no code required)**  
Vary well width → record energies → build a table → plot and interpret. Examine the model's assumptions and limits. Capstone: fit a curve to predict E(width) and test it against the solver — building a surrogate model, which is how machine learning is actually used in semiconductor and fusion workflows.

**Tier 2 — Applied programming**  
The source is written to be read. Run predict–modify–observe cycles (e.g., change grid spacing; observe numerical artifacts). Find a planted bug. Script batch runs across 50 well widths. Programming *against* real scientific code, not toy exercises.

**Tier 3 — Computational physics**  
Modify the algorithm: implement the effective-mass discontinuity properly; compare shooting-method convergence; compute transition energies. Authorship capstone: reuse the solver skeleton for a new potential (harmonic well, double well). The resulting artifact is assessable evidence of the modifier-to-author transition.

---

## The model's limitations (stated honestly)

- One-dimensional, zero-temperature, abrupt interfaces
- Effective-mass approximation (single parabolic band)
- Does not account for band non-parabolicity, many-body effects, or strain
- Barrier offset coefficient (0.748x) is an estimate; values in the literature vary

These limitations are features for pedagogy: learners are asked to identify where the model breaks and why a model is not reality.

---

## Citing this work

If you use Wavewell in teaching or research, please cite it as:

> Venceslau, G. M. (2026). *Wavewell: an open browser-based quantum-well Schrödinger simulator for teaching computational physics* (v0.1.1). [https://doi.org/10.5281/zenodo.21361266](https://doi.org/10.5281/zenodo.21361266)

A `CITATION.cff` file is included in this repository for automated citation tools.

---

## License

MIT License © 2026 Gustavo Mulim Venceslau

Permission is granted, free of charge, to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of this software. See `LICENSE` for the full text.

Publishing under MIT does not transfer authorship or copyright. Derivative works should credit the original author per the terms above.

---

## Contributing

This project is in early development. Contributions, bug reports, and suggestions are welcome via GitHub Issues.

Priority items on the roadmap:
- In-browser live code editor (Tier 2 enabler — the biggest current gap)
- Plasma PIC Sandbox (second vertical slice)
- Curriculum module wrappers (guided-inquiry activity sequences)
- Offline/bundled asset mode (no internet required)

This project follows the spirit of the [Open Source Physics](https://www.compadre.org/osp/) and [PICUP](https://www.compadre.org/PICUP/) communities.

---

## Contact

**Gustavo Mulim Venceslau**  
[GitHub: gustavomulim](https://github.com/gustavomulim)  
[ORCID: 0009-0005-6911-9223](https://orcid.org/0009-0005-6911-9223)
