# Analysis Workshop: Linear Mixed Models with R

This repository contains materials for an introductory workshop on Linear Mixed Models (LMMs) using R.

## Contents

- `lmm_presentation.qmd` - Quarto presentation introducing LMMs with eye-tracking data
- `download_data.R` - Function to download datasets from Google Drive
- `data/` - Eye-tracking datasets for the workshop (automatically downloaded)
  - `Hindi_new.csv` - Hindi reading time data with factorial design (word type × frequency)
  - `RASTROS_sample.csv` - Portuguese reading data with continuous word frequency predictor

## Requirements

To run this presentation, you'll need:

- R (>= 4.0.0)
- Quarto
- Required R packages:
  - tidyverse
  - lme4
  - lmerTest
  - gghalves
  - broom.mixed

## Installation

### Downloading Data Files

The presentation automatically downloads required data files from Google Drive when you run it. The data files are:
- `Hindi_new.csv` - Downloaded from Google Drive
- `RASTROS_sample.csv` - Downloaded from Google Drive

The download function checks if files already exist and only downloads them if they're not present. To manually download the data files, you can run:

```r
source("download_data.R")
download_workshop_data()
```

To force re-download even if files exist:

```r
download_workshop_data(force_download = TRUE)
```

### Install R packages

```r
install.packages(c("tidyverse", "lme4", "lmerTest", "gghalves", "broom.mixed"))
```

### Install Quarto

Download and install Quarto from [https://quarto.org/docs/get-started/](https://quarto.org/docs/get-started/)

## Rendering the Presentation

To render the presentation to HTML (RevealJS):

```bash
quarto render lmm_presentation.qmd
```

To preview the presentation:

```bash
quarto preview lmm_presentation.qmd
```

## Workshop Overview

The presentation covers:

1. **Data Reading and Exploration**
   - Loading eye-tracking data with tidyverse's `read_csv()`
   - Descriptive statistics
   - Raincloud plots using gghalves

2. **Hindi Data - Factorial Design**
   - Setting up two-factor design (word type × frequency)
   - Sum contrasts coding
   - Fitting LMMs with interactions
   - Interpreting factorial effects

3. **RASTROS Data - Continuous Predictors**
   - Fitting LMMs with continuous predictors (word frequency)
   - Interpreting slopes
   - Visualizing relationships

4. **Advanced Considerations**
   - Random slopes vs. random intercepts
   - Power considerations (Brysbaert & Stevens, 2018)
   - Multiple comparisons issues
   - Extracting statistics for inline reporting

## Data Description

### Hindi Data (Hindi_new.csv)

Eye-tracking data from Hindi reading with factorial design:

- **RECORDING_SESSION_LABEL**: Participant ID
- **cond_name**: Condition code (RL, RH, TL, TH)
  - RL = Romance Low Frequency
  - RH = Romance High Frequency
  - TL = Traditional Low Frequency
  - TH = Traditional High Frequency
- **IA_FIRST_FIXATION_DURATION**: First fixation duration (ms)
- **IA_DWELL_TIME**: Total dwell time (ms)
- Other eye-tracking measures

### RASTROS Data (RASTROS_sample.csv)

Portuguese reading data with word-level predictors:

- **RECORDING_SESSION_LABEL**: Participant ID
- **IA_FIRST_FIXATION_DURATION**: First fixation duration (ms)
- **Freq_Brasileiro_log**: Log word frequency in Brazilian Portuguese
- **Word_Length**: Number of characters
- **Content_or_Function**: Word class
- Other eye-tracking and linguistic measures

## License

This material is provided for educational purposes.