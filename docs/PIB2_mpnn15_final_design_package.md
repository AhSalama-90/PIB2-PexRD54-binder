# PIB2 — Final Design Package
## PIB2_l106_s877252_mpnn15

---

## 1. Target & Mechanism

**Target:** PexRD54, an RXLR-type effector secreted by *Phytophthora infestans* (Irish potato famine pathogen).

**Mechanism of pathogenicity:** PexRD54 binds host ATG8CL via its C-terminal ATG8-family Interacting Motif (AIM), antagonizing the host autophagy cargo receptor Joka2 and perturbing plant selective autophagy defense (Dagdas et al., 2016, *eLife*; Maqbool et al., 2016, *J Biol Chem*).

**Design strategy:** *De novo* protein binder engineered to occlude the AIM motif (residues 372–381) via steric occlusion, preventing PexRD54–ATG8CL association.

**Critical anchor residues (per Maqbool et al., 2016):**
- **W378** — alanine substitution (W378A) completely abolished ATG8CL binding (SPR, gel filtration)
- **V381** — alanine substitution (V381A) did NOT abolish binding; less critical anchor, but occupies a distinct hydrophobic pocket on ATG8CL

---

## 2. Design Method

- **Backbone/interface hallucination:** BindCraft (AlphaFold2-multimer-based), Pacesa et al., *Nature* 2025 (originally bioRxiv 2024)
- **Sequence design:** ProteinMPNN
- Key pipeline settings: `weights_pae_inter=1.0`, `target_hotspot_residues=A372-381`, `lengths=[90,130]`

---

## 3. Final Sequence

**Protein (106 aa):**
```
GIQEFKELYRKLTKKQRRKVNDDMRWVYMWFMWEKRTHPNGKMYKELKKMFEKFAKKVVELLKGVEKPSEEQLEEISEIFKKIFMEYMKKYAPKWEVEHWEEMFNM
```

**DNA, E. coli codon-optimized, with stop codon (321 nt):**
```
GGCATCCAGGAATTCAAAGAACTGTATCGTAAACTGACCAAAAAACAGCGTCGTAAAGTGAACGATGATATGCGTTGGGTGTATATGTGGTTCATGTGGGAAAAACGTACCCATCCGAACGGCAAAATGTATAAAGAACTGAAAAAAATGTTCGAAAAATTCGCGAAAAAAGTGGTGGAACTGCTGAAAGGCGTGGAAAAACCGAGCGAAGAACAGCTGGAAGAAATCAGCGAAATCTTCAAAAAAATCTTCATGGAATATATGAAAAAATATGCGCCGAAATGGGAAGTGGAACATTGGGAAGAAATGTTCAACATGTAA
```
*Note: preliminary codon assignment using most-frequent E. coli codons; recommend final optimization via Twist's in-house tool before synthesis.*

---

## 4. Structural Validation Summary

| Check | Result |
|---|---|
| i_pTM / i_pAE (BindCraft native scoring) | Strong (passed all base + interface filters) |
| W378 contact — 5 independent AF2-multimer models | 2.2–3.5 Å (relaxed & unrelaxed) |
| V381 contact — 5 independent AF2-multimer models | 2.5–3.5 Å (relaxed & unrelaxed) |
| Both anchors covered simultaneously | Yes, 5/5 models |
| Independent raw-data recomputation | Confirmed identical to reported values |
| Interface residue pairs (<4.5 Å) | 87 |
| Hydrogen-bond-like contacts | 19 |
| Salt bridges | 3 |
| Hydrophobic contacts | 153 |
| Severe steric clashes (<2.0 Å) | 0 |
| Borderline contacts (2.0–2.4 Å) | 20, all attributable to one Phe(A60)/Trp(B33) aromatic ring stacking pair — not a genuine clash |
| One apparent unrelaxed-model clash (0.95 Å, model_5) | Resolved to 3.02 Å after Amber relaxation |

---

## 5. Physicochemical Properties

| Property | Value |
|---|---|
| Molecular weight | 13,453.8 Da |
| pI | 9.40 |
| GRAVY | −1.020 (highly hydrophilic / favorable solubility) |
| Instability Index | 51.44 (>40; common for de novo helical-bundle binders, not necessarily indicative of real instability) |
| Aromaticity | 0.160 |
| Cysteine count | 0 |
| **Methionine count** | **9/106 (8.5%) — elevated; flagged as a manufacturability/oxidation-risk caveat** |

---

## 6. Novelty Assessment

- **BLAST (NCBI ClusteredNR):** No significant similarity found — sequence is fully novel.
- **Literature search (PubMed, Europe PMC, OpenAlex, Crossref, targeted queries):** No prior published work found combining PexRD54 with de novo protein binder design or AIM-motif steric occlusion strategies.
- **Patent search:** One related patent identified (EP4170039A1, Sainsbury Laboratory, "Pikobody" nanobody-NLR fusion system) — mechanistically and functionally distinct: recognizes PexRD54 via an artificial GFP/mCherry tag to trigger immune activation, not via direct recognition of the native AIM motif for steric occlusion.

**Novelty statement (suggested):** *"To our knowledge, this represents the first de novo protein binder designed to directly occlude the AIM motif of PexRD54, shifting from mechanistic characterization (Maqbool et al., 2016) toward a molecular intervention strategy."*

---

## 7. Known Limitations (for transparent disclosure)

1. Computational/predictive evidence only — no experimental (in vitro or in planta) validation yet performed.
2. Elevated methionine content (8.5%) may pose oxidation-related stability concerns during long-term storage; does not affect predicted binding geometry.
3. Codon optimization is preliminary; final optimization recommended via synthesis vendor's tool.
