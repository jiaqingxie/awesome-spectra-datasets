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

## Dataset Index

Priority rule:

- Prefer a direct dataset/database link
- If there is no stable dataset landing page, use the paper link
- Keep benchmark datasets and legacy databases together, but label them clearly

| Dataset | IR | Raman | UV-Vis | NMR | MS / MS-MS | Type | Dataset Link | Paper / Reference |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SDBS | ✓ | ✓ |  | ✓ | ✓ | Experimental database | [SDBS](https://sdbs.db.aist.go.jp/) | [Introduction](https://sdbs.db.aist.go.jp/Htmls/Introduction_eng.html) |
| NIST Chemistry WebBook | ✓ |  | ✓ |  | ✓ | Experimental database | [WebBook Chemistry](https://webbook.nist.gov/chemistry/) | [WebBook](https://webbook.nist.gov/) |
| nmrshiftdb2 |  |  |  | ✓ |  | Mixed database | [nmrshiftdb2](https://nmrshiftdb.nmr.uni-koeln.de/nmrshiftdb/) |  |
| HMDB |  |  |  | ✓ | ✓ | Mixed database | [HMDB databases](https://hmdb.ca/w/databases) |  |
| BMRB small molecules |  |  |  | ✓ |  | Experimental database | [BMRB small molecules](https://bmrb.io/data_library/small_molecules.shtml) | [Metabolomics standards](https://bmrb.io/metabolomics/metabolomics_standards.php) |
| MassBank |  |  |  |  | ✓ | Experimental database | [MassBank](https://massbank.eu/MassBank/) | [NAR 2025](https://academic.oup.com/nar/advance-article-abstract/doi/10.1093/nar/gkaf1193/8321203) |
| MoNA |  |  |  |  | ✓ | Aggregated database | [MoNA](https://mona.fiehnlab.ucdavis.edu/) | [MANA databases](https://www.metabolomicsna.org/mana-databases) |
| GNPS Public Libraries |  |  |  |  | ✓ | Experimental library | [GNPS Libraries](https://gnps.ucsd.edu/ProteoSAFe/libraries.jsp) |  |
| QM9S | ✓ | ✓ | ✓ |  |  | Computational benchmark | [QM9S dataset](https://figshare.com/articles/dataset/QM9S_dataset/24235333) | [Nat Comput Sci 2023](https://www.nature.com/articles/s43588-023-00550-y) |
| QMe14S | ✓ | ✓ |  | ✓ |  | Computational benchmark |  | [JPC Letters 2025](https://pubs.acs.org/doi/10.1021/acs.jpclett.5c00839) |
| QM9NMR |  |  |  | ✓ |  | Computational benchmark | [QM9NMR](https://moldis-group.github.io/qm9nmr/) |  |
| ChEMBL IR/Raman extension | ✓ | ✓ |  |  |  | Computational dataset |  | [Scientific Data 2025](https://www.nature.com/articles/s41597-025-05289-x) |
| ORNL_AISD-Ex / GDB-9-Ex |  |  | ✓ |  |  | Computational dataset |  | [Scientific Data 2023](https://www.nature.com/articles/s41597-023-02408-4) |
| API Raman dataset |  | ✓ |  |  |  | Experimental dataset |  | [Scientific Data 2025](https://www.nature.com/articles/s41597-025-04848-6) |
| UV/Vis comparative dataset |  |  | ✓ |  |  | Mixed dataset |  | [Scientific Data 2019](https://www.nature.com/articles/s41597-019-0306-0) |

## Paired IR-Raman Datasets

For public small-molecule datasets where the same molecule is explicitly associated with both `IR` and `Raman`, the main benchmark-style resources are:

| Dataset | IR | Raman | Other Modalities | Link |
| --- | --- | --- | --- | --- |
| QM9S | ✓ | ✓ | UV-Vis | [QM9S dataset](https://figshare.com/articles/dataset/QM9S_dataset/24235333) |
| QMe14S | ✓ | ✓ | NMR | [JPC Letters 2025](https://pubs.acs.org/doi/10.1021/acs.jpclett.5c00839) |
| ChEMBL IR/Raman extension | ✓ | ✓ |  | [Scientific Data 2025](https://www.nature.com/articles/s41597-025-05289-x) |
| SDBS | ✓ | ✓ | NMR, EI-MS | [SDBS](https://sdbs.db.aist.go.jp/) |

The first three are the clearest modern ML-style paired `IR + Raman` resources. `SDBS` is also useful, but it is better viewed as a legacy spectral database than a pre-packaged benchmark dataset.

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
