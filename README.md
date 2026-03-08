# Claude Code Skills

A collection of Claude Code skills for computational materials science workflows.

## Skills

### [Defect-calculation](./Defect-calculation/)

Expert assistant for **point defect calculations** in semiconductors and insulators using VASP.

**Covers the full workflow:**

1. **Supercell Construction** - Build nearly-cubic supercells from primitive cells
2. **Bulk Relaxation** (ISIF=3) - Full cell + ion relaxation
3. **Defect Structure Generation** - Vacancies, antisites, substitutional impurities, defect complexes
4. **Neutral Defect Relaxation** (ISIF=2) - Ion-only relaxation at q=0
5. **Charge State Determination** - EIGENVAL analysis to identify defect levels and possible charge states
6. **Charged Defect Relaxation** - Relaxation with NELECT set for each charge state
7. **Static Calculations** - Single-point with LVHAR, ICORELEVEL for corrections
8. **Finite-Size Corrections** - Freysoldt (FNV) / Kumagai correction for charged defects
9. **Formation Energy Diagram** - E_f vs Fermi level with chemical potential limits

**Key features:**
- Strict step-by-step dependency management (no premature input file preparation)
- Automated SLURM job monitoring (`auto_monitor.sh`) with 10-min interval checks
- Optional `--claude` flag for AI-powered calculation result review
- Detailed operation logging to `defect_workflow.log`
- Python helper for automated defect structure construction

**Directory structure:**
```
ProjectRoot/
├── Bulk/
│   ├── relax/
│   └── statics/
├── Defect/
│   ├── Intrinsic/
│   │   └── V_Cd/
│   │       ├── q0/
│   │       │   ├── relax/
│   │       │   └── statics/
│   │       ├── q-1/
│   │       │   ├── relax/
│   │       │   └── statics/
│   │       └── ...
│   └── Impurity/
│       └── ...
├── ThermoStability/
└── FormationEnergy/
```

**Files:**
- [`SKILL.md`](./Defect-calculation/SKILL.md) - Main skill definition
- [`references/`](./Defect-calculation/references/) - Detailed reference documents
  - `chemical-potentials.md` - Stability region determination
  - `formation-energy-and-corrections.md` - Formation energy terms and FNV/Kumagai corrections
  - `formation-energy-diagram.md` - Plotting and thermodynamic analysis
  - `workflow-automation.md` - SLURM job scripts and monitoring

## Installation

To use a skill in Claude Code, copy it to your skills directory:

```bash
# Copy Defect-calculation skill
cp -r Defect-calculation/ ~/.claude/skills/defect-calculation/
```

Then invoke with `/defect-calculation` in Claude Code.

## License

MIT
