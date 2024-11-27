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
```

## Steps to Process the Data

### Step 1: Dataset Cleaning
- **Input**: `rounds(in)_sorted by D and H (rounds(in)).csv`.
- **Objective**: Structure and clean the raw data by parsing nested fields, splitting rows by roles, and renaming ambiguous columns.
- **Output**: Saved as `tangram.csv`.

---

### Step 2: Language Tagging
- **Input**: `tangram.csv`.
- **Objective**: Apply language tagging rules to annotate utterances with appropriate language tags based on the following predefined categories:

| **Tag**    | **Description**                                                                                  |
|------------|--------------------------------------------------------------------------------------------------|
| `E`        | Entirely English.                                                                               |
| `S`        | Entirely Spanish.                                                                               |
| `SE`       | Mixed starting with Spanish.                                                                    |
| `ES`       | Mixed starting with English.                                                                    |
| `P`        | Proper noun (e.g., names of places, people, institutions).                                       |
| `EP/SP`    | Proper noun at the end of an IU in English or Spanish.                                           |
| `D`        | Discourse marker or backchannel (e.g., "so," "you know"), ambiguous when near Spanish.           |
| `F`        | Filler sounds (e.g., "uh," "eh"), language-neutral.                                             |
| `N`        | Neutral "no" at language switch points.                                                         |
| `A`        | Non-linguistic sounds (e.g., laughter, coughing).                                               |
| `X`        | Unclear or unintelligible speech.                                                               |
| `L`        | Lone item, single word from one language in another, often nouns.                               |
| `SLS/ELE`  | Lone item followed by the same language.                                                        |

- **Output**: Saved as `tangrams_v0.csv`.

---

### Step 3: Merging with Metadata
- **Inputs**:
  - `tangrams_v0.csv`: Annotated dataset with utterance-level information.
  - `tidy_data.csv`: Dataset containing additional metadata (e.g., game, player, and round identifiers).
- **Objective**: Merge the two datasets based on shared keys:
  - `Game ID` in `tangrams_v0.csv` ↔ `game_id` in `tidy_data.csv`.
  - `Stage ID` in `tangrams_v0.csv` ↔ `stage_id` in `tidy_data.csv`.
- **Output**: Saved as `merged_tidy.csv`.

---

### Step 4: Adding Role-Based Utterance Counts
- **Input**: `merged_tidy.csv`.
- **Objective**: Add two new columns:
  - `Director Count`: Number of utterances by the `director` for each game.
  - `Matcher Count`: Number of utterances by the `matcher` for each game.
- **Output**: Saved as `merged.csv`.

---

### Step 5: Reapplying Language Tagging
- **Input**: `merged.csv`.
- **Objective**: Reapply language tagging rules to ensure consistency and address debugging issues. The same tagging rules as in Step 2 were used.
- **Output**: Saved as `merged_retag.csv`.
- 
The final dataset (merged_retag.csv) includes the following columns:

| **Column Name**       | **Description**                                                   |
|------------------------|-------------------------------------------------------------------|
| `Stage ID`            | Identifier for the stage within a game.                          |
| `Game ID`             | Identifier for the game session.                                 |
| `Trial Number`        | The trial number within the game.                                |
| `Repetition Number`   | The repetition number for the trial.                             |
| `Text`                | Utterance text from the speaker.                                 |
| `Player ID`           | Identifier for the player making the utterance.                 |
| `Target`              | The target object in the game.                                   |
| `Role`                | Role of the player (`director` or `matcher`).                   |
| `Language`            | The language tag applied to the utterance.                      |
| `Response`            | The response data for the utterance.                            |
| `Round Number`        | The round number within the session.                             |
| `game_id`             | Metadata column linking to `tidy_data.csv`.                     |
| `dyad_id`             | Metadata column for the dyad (pair of players).                 |
| `player_1_id`         | Identifier for Player 1.                                         |
| `player_2_id`         | Identifier for Player 2.                                         |
| `round_id`            | Identifier for the round.                                        |
| `stage_id`            | Metadata column linking to `tidy_data.csv`.                     |
| `game_start`          | Timestamp for the start of the game.                             |
| `Director Count`      | Number of utterances by the `director` in each round.            |
| `Matcher Count`       | Number of utterances by the `matcher` in each round.             |


