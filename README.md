# Tangrams Project: Data Processing Documentation

## Overview

This README outlines the steps taken to process the datasets used in the Tangrams project, culminating in the final file `merged_retag.csv`. The workflow includes cleaning raw data, annotating with language tags, merging datasets, adding role-based utterance counts, and reapplying language tagging due to debugging issues.

## Project Folder Structure

```plaintext
tangrams_project/
├── raw_data/
│   ├── rounds(in)_sorted by D and H (rounds(in)).csv  # Original messy dataset
│   ├── tidy_data.csv                                 # Dataset with additional metadata
├── processed_data/
│   ├── tangram.csv                                   # Cleaned intermediate dataset
│   ├── tangrams_v0.csv                               # Annotated dataset with language tags
│   ├── merged_tidy.csv                               # Merged dataset with tidy_data.csv
│   ├── merged.csv                                    # Dataset with utterance counts
│   ├── merged_retag.csv                              # Final dataset with re-applied language tagging
├── scripts/                                          # Data processing scripts
├── documentation/
│   ├── README.md                                     # This file

