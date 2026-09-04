# PIB2 — De Novo Protein Binder Targeting PexRD54

De novo mini-protein binder computationally designed to sterically occlude the AIM (ATG8-family Interacting Motif) of **PexRD54**, an RXLR effector secreted by *Phytophthora infestans* (the Irish potato late-blight pathogen).

## Background

PexRD54 binds host ATG8CL via its C-terminal AIM motif (residues 372–381), antagonizing the plant autophagy cargo receptor Joka2 and suppressing host defense (Dagdas et al., 2016, *eLife*; Maqbool et al., 2016, *J Biol Chem*). This project designs a binder that occludes this motif to block the interaction.

## Lead Candidate: PIB2_l106_s877252_mpnn15

- **Length:** 106 aa
- **Critical anchor coverage:** Both Trp378 (2.2–3.5 Å) and Val381 (2.5–3.5 Å) contacted across 5 independent AlphaFold2-multimer models, before and after Amber relaxation
- **Novelty:** No significant BLAST hit against NCBI ClusteredNR; no prior literature or patent found combining PexRD54 with de novo binder design

See `docs/PIB2_mpnn15_final_design_package.md` for the full validation report.

## Method

- **Binder hallucination:** [BindCraft](https://github.com/martinpacesa/BindCraft) (AlphaFold2-multimer-based)
- **Sequence design:** ProteinMPNN
- **Independent validation:** ColabFold (5-model ensemble), Amber relaxation
- **Target hotspot:** A372–381 (AIM motif)

## Repository Structure

sequences/ Final protein + DNA sequences (FASTA)
structures/ PDB structures (lead design, backup, trajectory backbone)
validation/ BindCraft filter statistics (CSV)
settings/ BindCraft configuration (JSON)
docs/ Full validation report and project report


## Status

Computational design stage complete. No experimental (wet-lab) validation has been performed yet — all evidence presented is in silico.

## Author

Ahmed Salama — Biotechnology and Genetic Engineering, Helwan National University / AGERI
