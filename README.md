# Replicating Hansen (2015), "Punishment and Deterrence: Evidence from Drunk Driving"


## The paper and its headline claim

- **Paper:** Hansen, Benjamin. 2015. "Punishment and Deterrence: Evidence from Drunk Driving." *American Economic Review* 105(4): 1581–1617.
- **Identification strategy:** regression discontinuity.
- **Headline claim:** Having a BAC just over 0.08 lowers the chance of a repeat drunk-driving stop within four years by about 2 percentage points.(Table 3, Panel A)
- **My replication:** -0.0222 vs the paper's -0.021, a gap of -5.5%, as `python reproduce.py` prints it.

## Reproduce the headline table

Python 3.11 or newer. From the repository root:

```bash
python -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python reproduce.py
```

`python reproduce.py` is the one command. Once `MY_PAPER` is set in `download_data.py`,
it downloads the data if `data/` does not have it, runs `notebooks/01_positioning_and_replication.ipynb` and then
`notebooks/02_robustness.ipynb` top to bottom in a fresh kernel, and prints the headline
table from `output/headline_table.csv`. Executed copies of the notebooks, with their
outputs, go to `output/executed/`.

- **Expected runtime:** : about 30 seconds to run in the environment.

## Data: source and licence

- **Source:** https://raw.githubusercontent.com/scunning1975/mixtape/master/hansen_dwi.dta, from Scott Cunningham's repository. 
- **Included or downloaded:** Downloaded. `download_data.py` fetches the file on the first run which it stays small.

The template downloads by default: `.gitignore` excludes `data/*.dta`, and
`download_data.py` fetches the files on the first run. Two facts to check before you
decide:

- The five files from `scunning1975/mixtape` (castle, card, lee, hansen, abortion) are in a
  repository under an MIT-style licence that permits copies if its notice is kept. The
  underlying data were collected by the original authors.
- The Dehejia-Wahba files on `users.nber.org/~rdehejia` state no licence. Download them;
  do not commit them.

If you decide to include the data, delete the `data/*.dta` line from `.gitignore`, commit
the files with the licence notice, and say so above.

## Repository map

| Path | What it is |
|---|---|
| `reproduce.py` | The one command: runs the notebooks in name order, prints the headline table |
| `download_data.py` | Data URLs for the six papers; `python download_data.py --paper card` fetches one into `data/` |
| `notebooks/01_positioning_and_replication.ipynb` | Sections 1 and 2: positioning notes, the replication, the theirs-vs-mine table, the discrepancy log. **No AI.** |
| `notebooks/02_robustness.ipynb` | Section 3: four robustness exercises. AI allowed, logged in `ai-appendix.md` |
| `output/headline_table.csv` | The theirs-vs-mine table, written by notebook 01 |
| `output/` | Every table and figure the report uses |
| `report/` | The report PDF |
| `ai-appendix.md` | P.R.I.M.E. entries and full transcripts for Sections 3 to 6, and the no-AI statement for Sections 1 and 2 |
| `AUDIT.md` | How to run the peer audit you file on a classmate's repository |
| `requirements.txt` | Pinned package versions |


## Use of AI

Sections 1 and 2 were completed without AI.

I used AI as a co-pilot in section3,4,6 which under P.R.I.M.E.,see details in [`ai-appendix.md`](ai-appendix.md).

