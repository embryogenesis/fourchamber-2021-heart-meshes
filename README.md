# Rodero et al. 2021 — virtual cohort of adult four-chamber heart meshes

A **verbatim mirror** of [`10.5281/zenodo.4590294`](https://doi.org/10.5281/zenodo.4590294), redistributed under the terms of the licence the depositors chose. No file has been modified.

## Attribution

> Rodero, Cristobal; Strocchi, Marina; Marciniak, Maciej; Longobardi, Stefano; Whitaker, John; O'Neill, Mark D.; Gillette, Karli; Augustin, Christoph; Plank, Gernot; Vigmond, Edward J.; Lamata, Pablo; Niederer, Steven A.
>
> Rodero C, Strocchi M, Marciniak M, et al. Linking statistical shape models and simulated function in the healthy adult human heart. PLOS Computational Biology 17(4):e1008851 (2021), doi:10.1371/journal.pcbi.1008851. Data: Zenodo, doi:10.5281/zenodo.4590294.
>
> DOI: [10.5281/zenodo.4590294](https://doi.org/10.5281/zenodo.4590294) — licensed **CC BY 4.0**

Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/); see [`LICENSE`](LICENSE). You may share and adapt this material for any purpose, including commercially, provided you give appropriate credit, link to the licence and indicate if changes were made. **This mirror makes no changes.**

## What this is

Twenty four-chamber heart meshes segmented from end-diastolic CT, as ASCII VTK unstructured grids of tetrahedra with an average edge length of 1 mm and points in millimetres. Twenty-four element labels: the four chamber myocardia, the aortic and pulmonary artery walls, the four valve planes, and the inlets and borders of the four pulmonary veins, the two venae cavae and the left atrial appendage. Each mesh also carries rule-based ventricular fibre vectors, varying transmurally from 80 to -60 degrees, and four universal ventricular coordinates. This is the atlas's candidate for the adult end of the heart across the lifespan.

## Provenance of the material

Twenty patients who came to an emergency room with acute chest pain and in whom no cardiac condition was found on follow-up. The depositors' own words are that these patients "were taken as representative of 'healthy' (or asymptomatic) hearts" — so "healthy" in the title means asymptomatic on follow-up, which is the weaker claim, and the hedge is theirs rather than this project's. The deposit records no ethics statement or consent documentation of its own and this project has not established what applied.

## Contents

22 file(s), 1531.9 MB total.

| File | Size | SHA-256 |
| --- | --- | --- |
| `data/16.tar.gz` | 74.5 MB | `85ca99c11f0fb8ff…` |
| `data/20.tar.gz` | 69.6 MB | `348526bb6fcb91b2…` |
| `data/15.tar.gz` | 61.9 MB | `59c8e095a3defadc…` |
| `data/10.tar.gz` | 96.1 MB | `f5c130dfa2d7ef2e…` |
| `data/11.tar.gz` | 79.6 MB | `eb3dfabe4c30a91e…` |
| `data/12.tar.gz` | 59.5 MB | `31bf4de87f7b49c9…` |
| `data/14.tar.gz` | 94.7 MB | `58302a951a46f8d8…` |
| `data/13.tar.gz` | 84.9 MB | `62b32451464bb173…` |
| `data/19.tar.gz` | 70.4 MB | `e763e5683da4a48b…` |
| `data/simulation_output.csv` | 0.0 MB | `3f59ea2e6388aa37…` |
| `data/modes_weights.csv` | 0.0 MB | `929efd810f3e40be…` |
| `data/18.tar.gz` | 53.7 MB | `b50919a711dc3914…` |
| `data/17.tar.gz` | 70.1 MB | `a6aac90fbdddf534…` |
| `data/06.tar.gz` | 63.8 MB | `ed465189d3c35acd…` |
| `data/05.tar.gz` | 54.9 MB | `1c24680bd2dedc1f…` |
| `data/01.tar.gz` | 91.1 MB | `a89f4c667d56e49e…` |
| `data/02.tar.gz` | 103.2 MB | `a9c2e24928770473…` |
| `data/03.tar.gz` | 85.9 MB | `5c21bd551e365f1f…` |
| `data/07.tar.gz` | 61.4 MB | `d4a0b430694d21ec…` |
| `data/08.tar.gz` | 80.0 MB | `7d0e737462107a58…` |
| `data/04.tar.gz` | 102.6 MB | `c7fc82b239d8e64e…` |
| `data/09.tar.gz` | 74.2 MB | `4a227cf5e27680c1…` |

Full checksums, original filenames and the source article id for every file are in [`MANIFEST.json`](MANIFEST.json).

## Notes for anyone using this

- IMPORTANT: the statistical shape model itself is not in this deposit. What is here is `modes_weights.csv`, the PCA mode weights for the nineteen meshes used to build it — mesh #20 was excluded. The mean shape and the extreme cases are a separate deposit, 10.5281/zenodo.4593739, and a further thousand generated meshes are 10.5281/zenodo.4506930; both are CC BY 4.0 and neither is mirrored here. Anyone expecting to generate a heart from this repository cannot.
- Twenty per-mesh archives `01.tar.gz` to `20.tar.gz` plus two CSVs: 1,531,867,710 bytes over 22 files, read from the Zenodo API. The largest, `02.tar.gz`, is 103,184,737 bytes — 98.4 MiB, clearing GitHub's 100 MiB hard limit by 1.6 MiB. That is the narrowest margin in this manifest, and all twenty archives are above GitHub's 50 MiB warning threshold, so `useReleaseAssets` is false on a measurement rather than on comfort.
- Simulation output is missing for two of the twenty. The depositors state that the electro-mechanical simulations of meshes #09 and #10 failed to converge and were not included in `simulation_output.csv`, so that file covers eighteen cases where the mesh set covers twenty.
- Universal ventricular coordinates are defined on the ventricles only. Every non-ventricular label carries -10 in all four coordinate fields, which is a sentinel and not a position.
- The deposit's description calls each per-mesh archive a "zipped folder"; they are gzipped tar.
- Adult hearts reconstructed from CT, where the embryonic end of this row is Faber's sectioned Carnegie material. Nothing in the deposit bridges the two, and this mirror asserts no correspondence between them.

## Verifying the mirror

```sh
# every file, against the manifest
python3 -c "import json,hashlib,pathlib;m=json.load(open('MANIFEST.json'));[print(('ok  ' if hashlib.sha256(pathlib.Path(f['path']).read_bytes()).hexdigest()==f['sha256'] else 'BAD ')+f['path']) for f in m['files'] if pathlib.Path(f['path']).exists()]"
```

---

Mirrored 2026-11-23 by `tools/mirror.ts` from [embryogenesis](https://github.com/embryogenesis/embryogenesis). The licence of each source record was checked against the live Zenodo metadata (`metadata.license.id`) before download. A record stating no licence aborts the mirror rather than defaulting to one.
