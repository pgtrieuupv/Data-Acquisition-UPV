# Carbon & Phosphorus Cycling in a Forest Ecosystem
**This file purpose is to explain the project overview, data dictionary and how you can keep track of everything to explore the different dataset.**

Dataset: 
## Subject: Control (3 rings), Track (3 rings)

## microbe: storage (pool), changes over time (translocation), difference (flux), concentration by depth
--> Microbe compete for Phosphate
## Phosphate: storage (pool), changes over time (translocation), difference (flux), concentration by depth
--> Phosphorus concentration affect the CO2 sequestration by the forest (rings)
## Carbon: storage (pool), changes over time (translocation), difference (flux), concentration by depth

## Tree parameters: canopy, wood, soil + root (0-10cm, 10-30cm, 30-60cm)
--> Quantify the differences

## Workflows for code:
1. Boxplot to show the distribution of C-P-Tree-Microbe in general in 1 representative year (2012-2018)
2. Line
3. Column graph for the tree parameters visualization for the differences in detail for 1 treatment (Control vs Track) and merged line graph to compare them over time from 2012-2018.

**1. Description of Selected Data**

This project uses data from a long-term ecosystem study investigating the effects of a specific treatment on carbon and phosphorus cycling.

**Data Link: [" "]**

**Experimental Design:**

Subjects: 6 experimental forest "rings" (plots).

**Treatments:**

Control (3 rings)

Track (3 rings)

Timeframe: Annual measurements from 2012 to 2018.

**Data Structure:**
The data is expected to be in a "tidy" long format, where each row represents a single measurement. The main variables include:

**Year:** 2012-2018

**Ring_ID:** Identifier for the specific ring (1-6).

**Treatment:** Control or Track.

**Component:** The part of the ecosystem being measured (e.g., Canopy, Wood, Soil, Root, Microbe).

**Depth:** Soil depth, if applicable (0-10cm, 10-30cm, 30-60cm).

**Variable:** The specific metric being recorded (e.g., Carbon_Pool, Phosphate_Concentration, Microbe_Flux).

**Value:** The measured value for that variable.

## 2. Objectives, Questions, and Hypotheses

### Objectives

The primary objective is to quantify and compare the effects of the Track treatment versus the Control on the carbon and phosphorus cycles. We aim to understand the interplay between soil microbes, nutrient availability (P), and carbon sequestration in tree components.

**Research Questions**

How do the overall pools of Carbon (C), Phosphorus (P), and Microbes differ between the Control and Track rings across the entire study period?

How have these C, P, and Microbe pools changed over time (2012-2018) in each treatment group?

What is the relationship between the microbe population and the concentration of available phosphate in the soil?

What is the relationship between phosphate availability and the rate of carbon sequestration (e.g., C stored in Canopy and Wood)?

**Main Hypotheses**

***H1 (Competition):*** Microbe populations compete with trees for available phosphate. We hypothesize a negative correlation between microbe pool size and available soil phosphate.

***H2 (Nutrient Limitation):*** Phosphorus concentration positively affects CO2 sequestration. We hypothesize a positive correlation between phosphate availability and carbon storage in tree components.

***H3 (Treatment Effect):*** The Track treatment will result in significantly different C and P pool sizes and fluxes compared to the Control group by the end of the study period.

## 3. Proposed Analysis Plan

We will follow a multi-step workflow to visualize patterns and statistically validate our findings.

**1. Overall Distribution (Faceted Boxplots)**

**Goal:** See the overall effect of the Track treatment on C, P, and Microbe variables, aggregated across all years.

**Method:** Create faceted boxplots.

**Y-axis:** Value (e.g., Concentration, Pool Size)

**X-axis:** Treatment (Control, Track)

**Facets:** Separate plots by Variable (C, P, Microbe) and Depth.

## 2. Changes Over Time & Summary (Line + Bar Charts)

**Goal (A):** Compare the change in C, P, and Tree parameters from 2012-2018.

**Method (A):** Create time-series line graphs with shaded standard error bands.

**X-axis:** Year

**Y-axis:** Mean Value

**Color:** Treatment (one line for Control, one for Track)

**Goal (B):** "Quantify the differences" in the final or average state.

**Method (B):** Create grouped bar charts with error bars.

**X-axis:** Parameter (e.g., "Canopy C," "Soil P 0-10cm")

**Y-axis:** Mean Value (averaged over the final years)

**Bars:** Side-by-side bars for Control vs. Track.

## 3. Hypothesis Testing (Scatter Plots)

**Goal:** Directly test our H1 and H2.

**Method:** Create scatter plots with regression lines.

**Plot H1 (Microbe vs. P):** 
**X-axis:** Microbe_Pool, **Y-axis:** Phosphate_Pool.

**Plot H2 (P vs. C):**
**X-axis:** Phosphate_Pool, **Y-axis:** Carbon_Flux (or Canopy_Carbon_Pool).

We will color the points by Treatment to check if the relationship itself differs.

## 4. Statistical Validation (Models)

**Goal:** Formally prove the patterns observed in the plots.

**Method (A):** Linear Mixed-Effects Models (LMM). This is the core analysis for Steps 1 and 2. It will allow us to test the (fixed) effects of Treatment, Year, and their interaction, while accounting for the (random) effect of Ring_ID (since measurements from the same ring are not independent).

**Method (B):** Linear Regression / ANCOVA. This will be used in Step 3 to get the R-squared and p-value for the relationships in our scatter plots, and to test if the slopes differ by treatment.
