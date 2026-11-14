# Setup

## Requirements

- Docker Engine with the Compose plugin.
- About 4 GB of RAM free for the container (Splunk will not finish starting without it).
- About 5 GB of disk for the image plus the indexed tutorial data.

## 1. Configure the password

```bash
cp .env.example .env
```

Edit `.env` and set a password of at least 8 characters. Admin login is `admin` plus this password.

## 2. Start Splunk

```bash
docker compose up -d
```

The first start pulls a ~1.8 GB image and initialises the volumes, so give it a few minutes.

## 3. Wait until it is healthy

```bash
docker compose ps
```

Wait for the `splunk` service to report `healthy` (the healthcheck allows a 3-minute start period).

## 4. Log in

Open <http://localhost:8000> and log in as `admin` with the password from `.env`.

## 5. Create the tutorial index

Settings > Indexes > New Index.

- Index name: `tutorial`
- Leave the other defaults.

## 6. Get the data files

Download `tutorialdata.zip` and `Prices.csv.zip` from Splunk's documentation (the "Upload the tutorial data" page of the Search Tutorial) and place both files in `data/`. Do not unzip them.

## 7. Upload the data

For each file:

1. Settings > Add Data > Upload.
2. Select the zip file.
3. Set **Index** to `tutorial`.
4. Keep the detected sourcetype, review, then Submit.

## 8. Verify

In Search & Reporting, set the time range to **All time** and run:

```spl
index=tutorial | stats count by sourcetype
```

You should see the tutorial sourcetypes with non-zero counts.

## Stop and reset

```bash
docker compose down      # stop, keep indexed data
docker compose down -v   # stop and delete both volumes (wipes all data)
```
