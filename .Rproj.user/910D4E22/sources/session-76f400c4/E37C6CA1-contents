# ── Project: Dental Technology Trends in Clinical Trials ──
# ── Author: Sanya Chauhan ─────────────────────────────────
# ── Date: 2026 ────────────────────────────────────────────
# ── Description: Visualize technology trends ──────────────

library(tidyverse)

# ── 1. Load trend data ────────────────────────────────────

all_trends <- read_csv("data/all_trends.csv")

# Verify
glimpse(all_trends)

# ── 2. Main line chart — all categories over time ─────────
ggplot(all_trends, 
       aes(x = start_year, 
           y = n_trials, 
           color = category)) +
  geom_line(size = 1) +
  geom_point(size = 2) +
  labs(
    title = "Dental Technology Trends in Clinical Trials (2000-2024)",
    subtitle = "Based on 4,422 registered trials from ClinicalTrials.gov",
    x = "Year",
    y = "Number of Registered Trials",
    color = "Technology"
  ) +
  
  # ── 3. Bar chart — total trials per category ─────────────
  
  category_totals <- all_trends |>
  group_by(category) |>
  summarise(total = sum(n_trials))

ggplot(category_totals, 
       aes(x = reorder(category, -total), 
           y = total,
           fill = category)) +
  geom_bar(stat = "identity") +
  labs(
    title = "Total Dental Technology Trials by Category (2000-2024)",
    x = "Technology Category",
    y = "Total Registered Trials"
  ) +
  theme_minimal() +
  theme(legend.position = "none")

ggsave("output/category_totals.png", width = 8, height = 5, dpi = 300)
  theme_minimal() +
  theme(
    plot.title = element_text(size = 14, face = "bold"),
    legend.position = "bottom"
  )
# Save the chart
ggsave("output/trend_chart.png", width = 10, height = 6, dpi = 300)

# ── 4. AI trend zoomed in ─────────────────────────────────

ai_only <- all_trends |>
  filter(category == "AI")

ggplot(ai_only,
       aes(x = start_year, y = n_trials)) +
  geom_line(color = "steelblue", linewidth = 1) +
  geom_point(color = "steelblue", size = 3) +
  labs(
    title = "AI-Related Dental Clinical Trials Over Time",
    subtitle = "Showing rapid emergence after 2018",
    x = "Year",
    y = "Number of Registered Trials"
  ) +
  theme_minimal()

ggsave("output/ai_trend.png", width = 8, height = 5, dpi = 300)

# ── 5. Funder type chart ──────────────────────────────────

funder_summary <- read_csv("data/funder_summary.csv")

ggplot(funder_summary,
       aes(x = reorder(funder_category, -n_trials),
           y = n_trials,
           fill = funder_category)) +
  geom_bar(stat = "identity") +
  labs(
    title = "Dental Clinical Trials by Funder Type (2000-2024)",
    x = "Funder Category",
    y = "Number of Trials"
  ) +
  theme_minimal() +
  theme(legend.position = "none")

ggsave("output/funder_chart.png", width = 8, height = 5, dpi = 300)
all_trends <- read_csv("data/all_trends.csv")

ggplot(all_trends, 
       aes(x = start_year, y = n_trials, color = category)) +
  geom_line(linewidth = 1) +
  geom_point(size = 2) +
  labs(
    title = "Dental Technology Trends in Clinical Trials (2000-2024)",
    subtitle = "Based on 4,422 registered trials from ClinicalTrials.gov",
    x = "Year",
    y = "Number of Registered Trials",
    color = "Technology"
  ) +
  theme_minimal()

ggsave("output/trend_chart.png", width = 10, height = 6, dpi = 300)