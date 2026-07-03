# ── Project: Dental Technology Trends in Clinical Trials ──
# ── Author: Sanya Chauhan ─────────────────────────────────
# ── Date: 2026 ────────────────────────────────────────────
# ── Description: Analyze trends by category and year ──────

library(tidyverse)
library(lubridate)

# ── 1. Load classified data ───────────────────────────────

trials_classified <- read_csv("data/trials_classified.csv")

# Verify
nrow(trials_classified)

# ── 2. Extract year from start date ───────────────────────

trials_classified <- trials_classified |>
  mutate(start_year = year(start_date))

# Check year range
min(trials_classified$start_year, na.rm = TRUE)
max(trials_classified$start_year, na.rm = TRUE)

# ── 3. Filter to complete years only ──────────────────────

trials_filtered <- trials_classified |>
  filter(start_year >= 2000, start_year <= 2024)

nrow(trials_filtered)

# ── 4. Count trials per category per year ─────────────────

# Implants over time
implant_trend <- trials_filtered |>
  filter(is_implant == TRUE) |>
  group_by(start_year) |>
  summarise(n_trials = n()) |>
  mutate(category = "Implant")

# Laser over time
laser_trend <- trials_filtered |>
  filter(is_laser == TRUE) |>
  group_by(start_year) |>
  summarise(n_trials = n()) |>
  mutate(category = "Laser")

# AI over time
ai_trend <- trials_filtered |>
  filter(is_ai == TRUE) |>
  group_by(start_year) |>
  summarise(n_trials = n()) |>
  mutate(category = "AI")

# CAD/CAM over time
cadcam_trend <- trials_filtered |>
  filter(is_cadcam == TRUE) |>
  group_by(start_year) |>
  summarise(n_trials = n()) |>
  mutate(category = "CAD/CAM")

# Teledentistry over time
tele_trend <- trials_filtered |>
  filter(is_teledentistry == TRUE) |>
  group_by(start_year) |>
  summarise(n_trials = n()) |>
  mutate(category = "Teledentistry")

# Robotics over time
robotics_trend <- trials_filtered |>
  filter(is_robotics == TRUE) |>
  group_by(start_year) |>
  summarise(n_trials = n()) |>
  mutate(category = "Robotics")

# ── 5. Combine all categories into one dataset ────────────

all_trends <- bind_rows(
  implant_trend,
  laser_trend,
  ai_trend,
  cadcam_trend,
  tele_trend,
  robotics_trend
)

# Check result
glimpse(all_trends)
nrow(all_trends)

# Save
write_csv(all_trends, "data/all_trends.csv")

# ── 5. Funder type analysis ───────────────────────────────

funder_summary <- trials_classified |>
  filter(start_year >= 2000, start_year <= 2024) |>
  mutate(
    funder_category = case_when(
      str_detect(str_to_lower(funder_type), "industry") ~ "Industry",
      str_detect(str_to_lower(funder_type), "nih") ~ "NIH",
      str_detect(str_to_lower(funder_type), "other") ~ "Academic/Other",
      TRUE ~ "Unknown"
    )
  ) |>
  group_by(funder_category) |>
  summarise(n_trials = n())

write_csv(funder_summary, "data/funder_summary.csv")