# awesome-spectra-datasets

An awesome list of public datasets for small-molecule spectroscopy, with a first focus on `IR`, `Raman`, `UV-Vis`, `NMR`, and `MS`.

## Scope

This repository prioritizes:

- Small molecules first
- Publicly accessible datasets and databases
- Resources useful for search, curation, benchmarking, and machine learning
- Both experimental and computational spectra when they are practically useful

## Covered Modalities

- IR
- Raman
- UV-Vis
- NMR
- MS / MS-MS

## Current Core Resources

| Resource | Modalities | Type | Notes |
| --- | --- | --- | --- |
| SDBS | IR, Raman, 1H NMR, 13C NMR, EI-MS | Experimental | Classic multi-modal organic compound database |
| NIST Chemistry WebBook | IR, MS, UV-Vis | Experimental | Strong baseline for small-molecule lookup |
| nmrshiftdb2 | 1H NMR, 13C NMR | Mixed | Open NMR database for organic small molecules |
| HMDB | NMR, MS/MS, GC-MS | Mixed | Very important for metabolites and bio-related small molecules |
| BMRB small molecules | NMR | Experimental | Includes peak lists and raw NMR data |
| MassBank | MS/MS | Experimental | Open FAIR reference spectral database |
| MoNA | MS/MS, GC-MS | Aggregated | Large-scale mass spectral aggregation resource |
| GNPS Public Libraries | MS/MS | Experimental | Strong for natural products and community workflows |
| QM9S | IR, Raman, UV-Vis | Computational | Widely used quantum-chemical spectra benchmark on QM9 molecules |
| QMe14S | IR, Raman, NMR | Computational | Expanded spectral benchmark with 14 elements and broader functional-group coverage |
| QM9NMR | NMR | Computational | Large atom-resolved NMR shielding dataset for QM9 molecules |
| ChEMBL IR/Raman extension | IR, Raman | Computational | Large-scale computed spectra for ML |
| ORNL_AISD-Ex / GDB-9-Ex | UV-Vis | Computational | Large excited-state UV-Vis datasets |

## Files

- [small_molecule_spectra_datasets.md](./small_molecule_spectra_datasets.md): detailed Chinese summary with scale, strengths, limitations, and links

## First Release Plan

- Curate the public small-molecule datasets by modality
- Separate canonical databases from quantum-chemical benchmark families such as `QM9S`, `QMe14S`, and `QM9NMR`
- Normalize metadata fields across resources
- Separate experimental and computational datasets
- Add download/API/license notes
- Expand toward benchmark-ready tables

## Important Benchmark Families

These are especially useful for ML benchmarking and should be tracked separately from experimental reference databases:

| Family | Focus | Notes |
| --- | --- | --- |
| QM9S | IR, Raman, UV-Vis | Based on QM9; strong baseline for structure-to-spectrum learning |
| QMe14S | IR, Raman, NMR | Broader chemistry than QM9S with 14 elements and 47 functional groups |
| QM9NMR | NMR shielding | Atom-level NMR benchmark across 130k+ QM9 molecules |
| ORNL_AISD-Ex / GDB-9-Ex | UV-Vis excited states | Very large computed UV-Vis resources |
| ChEMBL IR/Raman extension | IR, Raman | Larger-scale computed IR/Raman resource beyond QM9-style chemistry |

## Suggested Metadata Schema

| Field | Meaning |
| --- | --- |
| dataset_name | Dataset or database name |
| modality | IR / Raman / UV-Vis / NMR / MS / MS2 |
| molecule_scope | Organic small molecules / metabolites / drugs / natural products |
| data_type | Experimental / computational / mixed |
| access | Web / bulk / API |
| record_unit | Compound-level / spectrum-level / peak-list-level |
| scale | Number of compounds / spectra / records |
| identifiers | SMILES / InChI / InChIKey / accession |
| metadata | Solvent / instrument / ion mode / collision energy / temperature |
| license | Open / restricted / mixed |

## Data Sources Included So Far

- [SDBS](https://sdbs.db.aist.go.jp/)
- [NIST Chemistry WebBook](https://webbook.nist.gov/chemistry/)
- [nmrshiftdb2](https://nmrshiftdb.nmr.uni-koeln.de/nmrshiftdb/)
- [HMDB](https://hmdb.ca/w/databases)
- [BMRB small molecules](https://bmrb.io/data_library/small_molecules.shtml)
- [MassBank](https://massbank.eu/MassBank/)
- [MoNA](https://mona.fiehnlab.ucdavis.edu/)
- [GNPS Spectral Libraries](https://gnps.ucsd.edu/ProteoSAFe/libraries.jsp)
- [QM9S dataset](https://figshare.com/articles/dataset/QM9S_dataset/24235333)
- [QMe14S paper](https://pubs.acs.org/doi/10.1021/acs.jpclett.5c00839)
- [QM9NMR](https://moldis-group.github.io/qm9nmr/)
- [ChEMBL IR/Raman dataset paper](https://www.nature.com/articles/s41597-025-05289-x)
- [API Raman dataset paper](https://www.nature.com/articles/s41597-025-04848-6)
- [UV/Vis comparative dataset paper](https://www.nature.com/articles/s41597-019-0306-0)
- [UV-Vis excited-state datasets paper](https://www.nature.com/articles/s41597-023-02408-4)

## Notes

- Counts and coverage can change over time.
- This repository currently starts from small molecules and public resources only.
- Commercial resources are intentionally excluded from the first pass.
