# ── Project: Dental Technology Trends in Clinical Trials ──
# ── Author: Sanya trials_clean.csv─────────────────────────
# ── Date: 2026 ────────────────────────────────────────────
# ── Description: Import and clean ClinicalTrials.gov data ─

library(tidyverse)
library(janitor)
library(lubridate)

# ── 1. Import raw data ────────────────────────────────────

trials_raw <- read_csv("data/ctg-studies.csv")

# Check dimensions
nrow(trials_raw)
ncol(trials_raw)

# First look
glimpse(trials_raw)

# ── 2. Clean column names ─────────────────────────────────

trials_raw <- trials_raw |>
  clean_names()

# Verify
glimpse(trials_raw)

# ── 3. Select relevant columns ────────────────────────────

trials_clean <- trials_raw |>
  select(
    nct_number,
    study_title,
    brief_summary,
    study_status,
    start_date,
    funder_type,
    sponsor,
    conditions
  )

# Verify selection
glimpse(trials_clean)

# ── 4. Fix date column ────────────────────────────────────

trials_clean <- trials_clean |>
  mutate(
    start_date = parse_date_time(
      start_date,
      orders = c("ymd", "ym"),
      quiet = TRUE
    ) |> as.Date()
  )

# Check date parsing results
sum(!is.na(trials_clean$start_date))  # successfully parsed
sum(is.na(trials_clean$start_date))   # still missing

# ── 5. Save clean data ────────────────────────────────────

write_csv(trials_clean, "data/trials_clean.csv")
file.exists("data/trials_clean.csv")
