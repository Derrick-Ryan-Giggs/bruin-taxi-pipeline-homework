# Bruin Homework

## Question 1 — Bruin Pipeline Structure

From the project structure in the docs, a Bruin project requires `.bruin.yml` at the root AND a `pipeline/` directory containing `pipeline.yml` and `assets/`.

**Answer:** `.bruin.yml` and `pipeline/` with `pipeline.yml` and `assets/`

---

## Question 2 — Materialization Strategies

The staging layer in the docs uses `time_interval` — it deletes rows in the time window then re-inserts, which is perfect for incremental processing by `pickup_datetime` with deduplication.

**Answer:** `time_interval` — incremental based on a time column

---

## Question 3 — Pipeline Variables

Since `taxi_types` is an array variable, you need to pass it as a JSON array. The docs show `--var` is the flag used.

**Answer:**
```bash
bruin run --var 'taxi_types=["yellow"]'
```

---

## Question 4 — Running with Dependencies

The `+` suffix on an asset name means "this asset and all downstream assets".

**Answer:**
```bash
bruin run --select ingestion.trips+
```

---

## Question 5 — Quality Checks

The docs show exactly this in the `payment_lookup.asset.yml` example — columns use `checks: - name: not_null`.

**Answer:** `not_null: true`

---

## Question 6 — Lineage and Dependencies

The docs mention "view the lineage tab" in the Bruin panel but for the CLI command, the answer is:

**Answer:**
```bash
bruin lineage
```

---

## Question 7 — First-Time Run

The docs explicitly cover this — `--full-refresh` processes data from scratch starting from `start_date`, creating tables fresh.

**Answer:** `--full-refresh`
