# splunk-tutorial-lab

A local Splunk environment for practising security searches against Splunk's tutorial dataset. The dataset contains web access logs, SSH auth logs, proxy logs and sales transactions, which is enough to practise ranking, error analysis, brute-force hunting and simple detection logic.

## Quick start

```bash
cp .env.example .env   # then set a real password
docker compose up -d
# open http://localhost:8000 and log in as admin
```

Full steps, including the `tutorial` index and data upload, are in [docs/setup.md](docs/setup.md). Data files are not bundled: download `tutorialdata.zip` and `Prices.csv.zip` from Splunk's documentation and put them in `data/`.

## Folders

- `searches/` - exploration queries. Each file is a question about the data, meant to be read and tweaked.
- `detections/` - candidate scheduled alert rules, with thresholds, schedules and false-positive notes in the header comment.
- `docs/` - setup instructions and a description of the dataset's sourcetypes.
- `notes/` - a findings template for each search and a short SPL cheatsheet.
- `dashboards/` - reserved for dashboard definitions exported from Splunk.
- `data/` - drop the tutorial zip files here; they are gitignored.

## Status

Phase 1: one Splunk instance and the tutorial dataset. The next phase grows this into a full SOC lab with Juice Shop, an Nginx reverse proxy, Suricata and Zeek feeding the same indexer.
