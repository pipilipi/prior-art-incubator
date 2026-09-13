Prior Art Incubator
A public archive of defensive disclosures, prior-art research, technical analyses, and experimental invention concepts.
The purpose of this repository is to develop technical ideas rigorously, test them against known physics and existing prior art, and publish sufficiently detailed disclosures when keeping the resulting knowledge in the public domain is more useful than pursuing exclusivity.
Method
Ideas are treated as hypotheses, not inventions by default.
A typical development cycle is:
Explore → Critique → Verify → Search prior art → Experiment → Publish
Claims that fail physical, mathematical, or prior-art review are discarded or narrowed. Unverified claims remain explicitly marked as experimental.
Typical status labels:
PREŽIVEO — survived the current technical audit
SPORAN — plausible, but novelty or another key claim remains uncertain
TRAŽI EKSPERIMENT — requires experimental validation
ODBAČEN — failed technical or prior-art review
Published disclosures
Project	Description	Status
Adaptive Perovskite Recovery PV	Concentrated perovskite photovoltaics using controlled light/dark recovery cycles, thermal management, and history-aware adaptive control	SPORAN / TRAŽI EKSPERIMENT
Adaptive Perovskite Recovery PV
The disclosed concept investigates whether perovskite photovoltaic material can produce more useful lifetime energy when regions of the active surface are repeatedly moved between concentrated illumination and controlled dark-recovery periods.
The system may track the illumination dose, temperature, dark time, electrical performance, and estimated state of health of individual photovoltaic regions and adapt exposure and recovery schedules accordingly.
Read the defensive disclosure
Repository structure
Each invention or research branch should normally have its own folder:
prior-art-incubator/
├── README.md
├── perovskite-recovery-pv/
│   ├── README.md
│   ├── defensive_disclosure_*.md
│   ├── *.sha256
│   ├── prior-art/
│   ├── calculations/
│   └── figures/
└── future-project/
    └── ...
A separate GitHub repository is only necessary when a branch becomes a substantial independent engineering project with its own code, CAD, experiments, or development lifecycle.
Publication integrity
Published disclosures may include a SHA-256 checksum so that a specific document version can later be verified.
Git commit history provides an additional public record of how the material evolved.
The publication date of a disclosure is the date on which the relevant technical content actually became publicly accessible. Files should not be backdated.
Prior-art policy
This repository does not assume that every published idea is novel.
Where relevant prior art is known, it should be identified explicitly and the remaining technical contribution narrowed accordingly.
The objective is to create technically useful, searchable disclosures that distinguish:
what was already known;
what is being newly proposed;
what has been demonstrated;
what remains hypothetical;
what experiment could confirm or falsify the proposal.
Legal note
Material in this repository is published for technical and defensive-disclosure purposes. It is not legal advice, a patentability opinion, or a patent application.
Public disclosure may affect patent rights. Anyone intending to seek patent protection should consider that before publishing technical material.
