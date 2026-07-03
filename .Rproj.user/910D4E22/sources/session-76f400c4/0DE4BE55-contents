# ── Project: Dental Technology Trends in Clinical Trials ──
# ── Author: Sanya Chauhan ─────────────────────────────────
# ── Date: 2026 ────────────────────────────────────────────
# ── Description: Classify trials into technology categories

library(tidyverse)

# ── 1. Load clean data ────────────────────────────────────

trials_clean <- read_csv("data/trials_clean.csv")

# Verify it loaded
nrow(trials_clean)
glimpse(trials_clean)
# ── 2. Create text search column ─────────────────────────

# Combine title and summary into one searchable text column
# We search both because titles are short and may miss keywords
trials_clean <- trials_clean |>
  mutate(
    search_text = str_to_lower(
      paste(study_title, brief_summary, sep = " ")
    )
  )

# Verify
glimpse(trials_clean)

# ── 3. Classify trials into technology categories ─────────

trials_classified <- trials_clean |>
  mutate(
    is_implant = str_detect(
      search_text,
      "implant|osseointegrat|implant-supported|dental implant"
    ),
    is_laser = str_detect(
      search_text,
      "laser|photobiomodulat|lllt|er:yag|low-level light"
    ),
    is_ai = str_detect(
      search_text,
      "artificial intelligence|machine learning|deep learning|computer-aided|neural network|algorithm"
    ),
    is_cadcam = str_detect(
      search_text,
      "cad/cam|cad cam|digital impression|3d print|intraoral scan|digital workflow"
    ),
    is_teledentistry = str_detect(
      search_text,
      "teledentistry|telehealth|remote consult|mhealth|mobile health|teleconsult"
    ),
    is_robotics = str_detect(
      search_text,
      "robot|robotic|autonomous system|computer-assisted surger"
    )
  )

# ── 4. Check how many trials per category ─────────────────

summarise(trials_classified,
          implant       = sum(is_implant, na.rm = TRUE),
          laser         = sum(is_laser, na.rm = TRUE),
          ai            = sum(is_ai, na.rm = TRUE),
          cadcam        = sum(is_cadcam, na.rm = TRUE),
          teledentistry = sum(is_teledentistry, na.rm = TRUE),
          robotics      = sum(is_robotics, na.rm = TRUE)
)
# ── 5. Save classified data ───────────────────────────────

write_csv(trials_classified, "data/trials_classified.csv")
file.exists("data/trials_classified.csv")