# Master Thesis Experiment Prototype and Data Submission

This repository contains the browser-based experiment prototype, cleaned datasets, final analysis notebook, generated figures, and backend documentation for my master thesis at the University of Amsterdam.

The experiment is part of the thesis project:

**Designing Uncertainty-Aware AI Interfaces: Verbal Hedging and Trust Calibration in Text and Synthetic Speech**

The live experiment prototype can be accessed through GitHub Pages:

**Experiment link:** [https://mandydamsteegt.github.io/Master_Thesis/](https://mandydamsteegt.github.io/Master_Thesis/)

The executable prototype file is stored in:

```text
prototype/executable/index.html
```

The final data analysis reported in the thesis was conducted using:

```text
data/scripts/Data Analyse Defi (4).ipynb
```

---

## Project purpose

The experiment investigates how people evaluate AI-generated answers and how interface design may influence trust, verification behaviour, and reliance decisions.

The study focuses on two design factors:

1. **Verbal hedging**  
   Whether the assistant uses uncertainty cues such as:

   ```text
   I think
   It seems that
   about
   roughly
   ```

2. **Output modality**  
   Whether answers are presented as:

   ```text
   Text only
   Text with synthetic speech
   ```

Participants complete a sequence of general-knowledge evaluation trials. On each trial, they see a question and an AI-generated answer. Some answers are intentionally correct and some are intentionally incorrect. Participants can accept the answer, reject it, or verify supporting information before making a final decision.

---

## Experimental design

The study uses a **2 × 2 between-subjects design**.

| Condition | Hedging | Modality |
|---|---|---|
| **C1** | No hedge | Text |
| **C2** | Hedge | Text |
| **C3** | No hedge | Speech + Text |
| **C4** | Hedge | Speech + Text |

Participants were assigned to one of these four conditions.

The final sample consisted of **72 participants**, with **18 participants per condition**. Each participant completed **30 main trials**, resulting in **2160 trial-level observations**.

---

## Repository structure

```text
.
├── README.md
│
├── analysis_outputs/
│   └── figures/
│       ├── manipulation_check_uncertainty_certainty.png
│       ├── hedging_effect_verification_correctness.png
│       ├── srq1_verification_by_hedging_and_correctness.png
│       ├── srq2_acceptance_incorrect_answers_by_condition.png
│       ├── srq3_interaction_hedging_modality_accuracy.png
│       ├── srq3_interaction_hedging_modality_verification.png
│       ├── srq4_final_accuracy_across_blocks.png
│       └── srq4_verification_rate_across_blocks.png
│
├── data/
│   ├── rawdata/
│   │   └── data tijdelijk.docx
│   │
│   ├── clean/
│   │   ├── ai_hedging_clean_participants.csv
│   │   ├── ai_hedging_clean_trials_long.csv
│   │   ├── ai_hedging_clean_interviews.csv
│   │   ├── ai_hedging_condition_summary.csv
│   │   ├── ai_hedging_block_summary.csv
│   │   └── ai_hedging_data_dictionary.csv
│   │
│   └── scripts/
│       └── Data Analyse Defi (4).ipynb
│
├── prototype/
│   └── executable/
│       └── index.html
│
├── ai_backhand_server/
│   ├── README_AI_Backend.md
│   ├── package.json
│   ├── package-lock.json
│   └── server.js
│
└── misc/
    ├── exclusion_or_data_quality_notes.txt
    └── participant_notes.csv
```

The `ai_backhand_server/` folder contains the backend service that was used during data collection. The backend files are grouped in this folder so that the frontend prototype, analysis files, and backend infrastructure remain clearly separated.

The `node_modules/` folder is not included in this repository. Backend dependencies can be installed locally from `package.json` by running `npm install` inside the `ai_backhand_server/` folder.

---

## Experiment access

The experiment prototype is available online through GitHub Pages:

[https://mandydamsteegt.github.io/Master_Thesis/](https://mandydamsteegt.github.io/Master_Thesis/)

The local executable version is included in this repository as:

```text
prototype/executable/index.html
```

The experiment can therefore be inspected or re-run in two ways:

1. Open the online GitHub Pages version.
2. Open the local `prototype/executable/index.html` file in a modern browser.

---

## Running the prototype locally

To run the prototype locally:

1. Download or clone this repository.
2. Open the following file in a modern browser:

   ```text
   prototype/executable/index.html
   ```

3. Start the study from the landing page.

Recommended browsers:

- Google Chrome
- Microsoft Edge
- Safari
- Firefox

Speech synthesis availability may differ between browsers and operating systems. For the speech conditions, audio playback should be enabled and the device volume should be set to a comfortable level.

---

## GitHub Pages

This repository is configured to host the experiment prototype through **GitHub Pages**.

The live experiment page is available at:

[https://mandydamsteegt.github.io/Master_Thesis/](https://mandydamsteegt.github.io/Master_Thesis/)

The executable version used for the digital submission is retained in:

```text
prototype/executable/index.html
```

Depending on the GitHub Pages configuration, a root-level `index.html` may be used to redirect or serve the hosted version, while the version in `prototype/executable/` remains the documented prototype file for inspection and submission.

---

## Experiment flow

The participant flow is:

1. **Landing page**
2. **Informed consent**
3. **Audio check for speech conditions**
4. **Instructions**
5. **Practice trials**
6. **Main task with 30 trials across 3 blocks**
7. **Manipulation checks**
8. **Trust questionnaire**
9. **NASA-TLX workload questionnaire**
10. **User Experience Questionnaire**
11. **Post-task questions**
12. **Final reflection questions**
13. **Debrief and data save**

---

## Measures

The prototype logs behavioural and questionnaire data.

### Behavioural measures

Behavioural measures include:

- assigned condition
- item ID
- block number
- trial index
- answer correctness
- displayed answer
- hedge phrase and hedge type
- verification behaviour
- evidence dwell time
- source-opening behaviour
- final accept or reject decision
- decision time
- final decision accuracy

### Questionnaire measures

Questionnaire measures include:

- manipulation checks for perceived uncertainty and certainty
- trust and perceived reliability items
- NASA-TLX workload items
- the full 26-item User Experience Questionnaire
- post-task reflection questions

---

## UEQ implementation

The prototype uses the **full 26-item User Experience Questionnaire**.

The original item wording, item order, seven-point semantic differential format, and polarity are preserved. To reduce visual load, the UEQ is presented across two consecutive pages:

- **Page 1:** items 1–13
- **Page 2:** items 14–26

No additional randomisation of UEQ items or polarity is applied.

UEQ item scores are transformed to the standard **-3 to +3 range**, where higher scores indicate a more positive user experience.

The six UEQ scales are:

- **Attractiveness**
- **Perspicuity**
- **Efficiency**
- **Dependability**
- **Stimulation**
- **Novelty**

---

## Admin interface

The prototype includes a hidden researcher interface for managing and inspecting experiment sessions.

The admin interface can be used to:

- start a participant session manually
- select manual or balanced condition assignment
- load locally saved sessions
- import participant JSON files
- export aggregated JSON data
- export trial-level CSV data
- inspect condition-level and item-level summaries

The admin interface is intended only as a lightweight researcher tool for this prototype and should not be treated as secure production authentication.

---

## Backend/server setup

During data collection, completed participant sessions were sent from the browser-based prototype to a backend server.

The backend files are stored in:

```text
ai_backhand_server/
```

This folder includes:

```text
ai_backhand_server/README.md
ai_backhand_server/package.json
ai_backhand_server/package-lock.json
ai_backhand_server/server.js
```

The backend was used to:

- receive completed participant sessions from the experiment prototype
- store submitted sessions as JSON files
- provide export routes for downloading the collected data
- support participant-level, trial-level, and qualitative data export
- keep data storage separate from the frontend prototype

The backend is documented for transparency about the data collection infrastructure. The final thesis analysis does **not** require the backend server to be running. The final reported results can be reproduced from the cleaned CSV files in `data/clean/` and the final analysis notebook in `data/scripts/`.

No private credentials, API keys, passwords, database connection strings, secret environment variables, or `node_modules/` files are included in this repository.

More details about the backend setup are provided in:

```text
ai_backhand_server/README.md
```

---

## Data storage and export

During data collection, participant data were stored through the experiment backend. The prototype attempted to send completed sessions to the backend endpoint configured in the code. As a fallback, data could also be stored locally in the browser.

At the start of the data processing workflow, the data were exported locally from the backend/server using the following routes:

```text
https://ai-hedging-backend.onrender.com/api/download-all
https://ai-hedging-backend.onrender.com/api/download-participants-csv
https://ai-hedging-backend.onrender.com/api/download-trials-csv
https://ai-hedging-backend.onrender.com/api/download-interviews-csv
```

These routes were used to download the raw and structured data exports from the server. The exported files were then stored locally and used as the basis for cleaning, structuring, and analysis.

| Export route | Purpose |
|---|---|
| `/api/download-all` | Full raw export of all participant sessions, including metadata, questionnaires, qualitative responses, and trial-level logs |
| `/api/download-participants-csv` | Participant-level CSV export |
| `/api/download-trials-csv` | Trial-level long-format CSV export |
| `/api/download-interviews-csv` | Qualitative reflection/interview response CSV export |

The final analysis does not require live access to the backend server. It can be reproduced from the locally stored cleaned CSV files and the final analysis notebook included in this repository.

---

## Data files

The repository includes raw and cleaned data files used for the thesis analysis.

### Raw data

The raw data export is stored in:

```text
data/rawdata/data tijdelijk.docx
```

This file contains the original participant-level data export obtained from the backend/server export route:

```text
https://ai-hedging-backend.onrender.com/api/download-all
```

The raw export contains all completed participant sessions and includes participant metadata, condition assignment, questionnaire responses, post-task responses, qualitative responses, and trial-level logs.

The server also provided structured CSV export routes for participant-level, trial-level, and qualitative response data:

```text
https://ai-hedging-backend.onrender.com/api/download-participants-csv
https://ai-hedging-backend.onrender.com/api/download-trials-csv
https://ai-hedging-backend.onrender.com/api/download-interviews-csv
```

The exported files were downloaded locally from the server and then used as the basis for the cleaned datasets in:

```text
data/clean/
```

The raw export includes, where applicable:

- participant ID
- source file name
- condition assignment
- condition label
- hedging condition
- modality condition
- informed consent status
- session start and end timestamps
- manipulation-check responses
- trust questionnaire responses
- NASA-TLX workload responses
- User Experience Questionnaire responses
- post-task responses
- qualitative reflection responses
- researcher notes
- number of completed trials
- session status
- practice trial completion status
- break durations
- trial-level logs
- displayed AI answer
- answer correctness
- hedge phrase and hedge type
- verification behaviour
- evidence panel usage
- source-opening behaviour
- final accept/reject decision
- decision time
- final decision accuracy
- voice-related metadata for speech conditions

Where applicable, information not required for reproducing the analysis was removed before long-term storage.

---

## From raw data to cleaned data

The cleaned data files were created from the backend/server exports. The cleaning process was documented alongside the final analysis workflow. The final analysis notebook uses the cleaned CSV files to reproduce the analyses and figures reported in the thesis.

```text
data/scripts/Data Analyse Defi (4).ipynb
```

The cleaning and preparation process consisted of the following steps:

1. **Exporting the raw and structured data from the backend/server**  
   Data were downloaded locally from the backend/server using the export routes for all data, participant-level data, trial-level data, and interview/reflection data.

2. **Checking the raw export**  
   The raw export was inspected to verify that participant sessions were complete and that the expected fields were present. This included checking participant metadata, condition assignment, trial logs, questionnaire responses, and qualitative responses.

3. **Checking sample size and condition balance**  
   The dataset was checked for the expected final sample size of **72 participants**. Condition balance was checked to verify that the four experimental conditions each contained **18 participants**:

   - **C1:** No hedge + Text
   - **C2:** Hedge + Text
   - **C3:** No hedge + Speech
   - **C4:** Hedge + Speech

4. **Checking trial completeness**  
   Each participant was expected to complete **30 main trials**. The final dataset therefore contained **2160 trial-level observations**.

5. **Creating the participant-level cleaned dataset**  
   Participant-level metadata and questionnaire data were extracted and structured into:

   ```text
   data/clean/ai_hedging_clean_participants.csv
   ```

   This file contains one row per participant and includes condition assignment, hedging condition, modality condition, manipulation-check responses, trust responses, NASA-TLX workload responses, UEQ responses, post-task responses, and participant-level summary measures.

6. **Creating the trial-level long-format cleaned dataset**  
   Trial logs were extracted and converted into long format, resulting in:

   ```text
   data/clean/ai_hedging_clean_trials_long.csv
   ```

   This file contains one row per participant-trial combination. It is the main dataset for the behavioural analyses. It includes item ID, block number, trial index, answer correctness, displayed answer, hedge phrase, hedge type, verification behaviour, evidence panel usage, final decision, decision time, and final accuracy.

7. **Creating the cleaned qualitative response dataset**  
   Open-text reflection and interview-style responses were extracted and stored in:

   ```text
   data/clean/ai_hedging_clean_interviews.csv
   ```

   This file contains participant-level qualitative responses used to support the interpretation of the behavioural results.

8. **Creating summary datasets**  
   Condition-level and block-level summary datasets were created for descriptive analysis and reporting:

   ```text
   data/clean/ai_hedging_condition_summary.csv
   data/clean/ai_hedging_block_summary.csv
   ```

   The condition summary file contains descriptive statistics per experimental condition. The block summary file contains descriptive statistics across the three repeated interaction blocks.

9. **Creating the data dictionary**  
   Variable names, labels, and coding conventions were documented in:

   ```text
   data/clean/ai_hedging_data_dictionary.csv
   ```

   This file explains the main variables used in the cleaned datasets and should be consulted before reproducing the analysis.

10. **Generating the final figures**  
    The cleaned datasets were used in `Data Analyse Defi (4).ipynb` to generate the final figures stored in:

    ```text
    analysis_outputs/figures/
    ```

The final cleaned data files are therefore derived from the backend/server exports and are the files used for the final thesis analysis.

---

## Cleaned data

The cleaned data files are stored in:

```text
data/clean/
```

The cleaned data files are:

```text
ai_hedging_clean_participants.csv
ai_hedging_clean_trials_long.csv
ai_hedging_clean_interviews.csv
ai_hedging_condition_summary.csv
ai_hedging_block_summary.csv
ai_hedging_data_dictionary.csv
```

### `ai_hedging_clean_participants.csv`

Participant-level cleaned dataset. Each row represents one participant.

This file includes participant-level information such as:

- participant ID
- condition
- condition label
- hedging condition
- modality condition
- manipulation-check responses
- trust questionnaire responses
- NASA-TLX workload responses
- UEQ responses
- post-task responses
- participant-level summary measures

### `ai_hedging_clean_trials_long.csv`

Trial-level long-format cleaned dataset. Each row represents one participant-trial observation.

This is the main dataset for the behavioural analyses.

This file includes trial-level variables such as:

- participant ID
- condition
- condition label
- hedging condition
- modality condition
- item ID
- block
- trial index
- answer correctness
- displayed AI answer
- hedge phrase
- hedge type
- verification behaviour
- evidence panel usage
- source-opening behaviour
- final decision
- decision time
- final accuracy
- question text

### `ai_hedging_clean_interviews.csv`

Cleaned qualitative reflection dataset. This file contains the open-text responses used to support the interpretation of the behavioural findings.

The qualitative responses cover topics such as:

- what strategy participants used when deciding to accept, reject, or verify
- whether hedging phrases were noticed
- whether modality influenced interpretation
- whether behaviour changed across blocks

### `ai_hedging_condition_summary.csv`

Condition-level summary file with descriptive statistics by experimental condition.

### `ai_hedging_block_summary.csv`

Block-level summary file with descriptive statistics across the three repeated interaction blocks.

This file was used to inspect behavioural adaptation over time, including changes in verification rate, final accuracy, and decision time across blocks.

### `ai_hedging_data_dictionary.csv`

Data dictionary explaining the variable names, labels, and coding conventions used in the cleaned datasets.

This file should be consulted before reproducing the analysis.

---

## Main coding conventions

### Condition coding

| Code | Condition |
|---|---|
| **C1** | No hedge + Text |
| **C2** | Hedge + Text |
| **C3** | No hedge + Speech + Text |
| **C4** | Hedge + Speech + Text |

### Hedging coding

| Value | Meaning |
|---|---|
| **0** | No hedge |
| **1** | Hedge |

### Modality coding

| Value | Meaning |
|---|---|
| **0** | Text |
| **1** | Speech + Text |

### Answer correctness coding

| Value | Meaning |
|---|---|
| **0** | Incorrect AI answer |
| **1** | Correct AI answer |

### Verification behaviour coding

| Value | Meaning |
|---|---|
| **0** | Participant did not verify |
| **1** | Participant verified/opened the evidence panel |

### Final accuracy coding

| Value | Meaning |
|---|---|
| **0** | Participant’s final answer was incorrect |
| **1** | Participant’s final answer was correct |

### Block coding

| Value | Meaning |
|---|---|
| **1** | Block 1 |
| **2** | Block 2 |
| **3** | Block 3 |

---

## Final analysis notebook

The final analysis was conducted in:

```text
data/scripts/Data Analyse Defi (4).ipynb
```

This notebook loads the cleaned datasets, performs the final descriptive and inferential analyses, and generates the figures used in the thesis.

The notebook performs the final analysis steps, including:

1. Loading the cleaned datasets.
2. Checking the sample size and condition balance.
3. Summarising participant counts per condition.
4. Calculating manipulation-check summaries.
5. Calculating verification rates by hedging and answer correctness.
6. Calculating verification rates by condition.
7. Calculating acceptance of incorrect answers by condition.
8. Calculating final accuracy by condition and modality.
9. Calculating interaction patterns between hedging and modality.
10. Calculating verification and final accuracy patterns across blocks.
11. Generating the final figures used in the thesis.

To reproduce the analysis, run `Data Analyse Defi (4).ipynb` from top to bottom.

The notebook assumes that the cleaned CSV files are available in:

```text
data/clean/
```

---

## Figures

The figures generated from the final analysis notebook are stored in:

```text
analysis_outputs/figures/
```

Included figures:

```text
manipulation_check_uncertainty_certainty.png
hedging_effect_verification_correctness.png
srq1_verification_by_hedging_and_correctness.png
srq2_acceptance_incorrect_answers_by_condition.png
srq3_interaction_hedging_modality_accuracy.png
srq3_interaction_hedging_modality_verification.png
srq4_final_accuracy_across_blocks.png
srq4_verification_rate_across_blocks.png
```

### Figure descriptions

#### `manipulation_check_uncertainty_certainty.png`

Shows perceived uncertainty and perceived certainty by hedging condition.

#### `hedging_effect_verification_correctness.png`

Shows the change in verification rate between the hedge and no-hedge conditions for correct and incorrect answers.

#### `srq1_verification_by_hedging_and_correctness.png`

Shows verification rates by hedging condition and answer correctness.

#### `srq2_acceptance_incorrect_answers_by_condition.png`

Shows the acceptance rate for incorrect AI answers across the four experimental conditions.

#### `srq3_interaction_hedging_modality_accuracy.png`

Shows the interaction between hedging and modality on final accuracy.

#### `srq3_interaction_hedging_modality_verification.png`

Shows the interaction between hedging and modality on verification rate.

#### `srq4_final_accuracy_across_blocks.png`

Shows final accuracy across the three interaction blocks by experimental condition.

#### `srq4_verification_rate_across_blocks.png`

Shows verification rate across the three interaction blocks by experimental condition.

---

## Reproducibility route

To reproduce the final reported analysis:

1. Open the cleaned data folder:

   ```text
   data/clean/
   ```

2. Review the data dictionary:

   ```text
   data/clean/ai_hedging_data_dictionary.csv
   ```

3. Open the final analysis notebook:

   ```text
   data/scripts/Data Analyse Defi (4).ipynb
   ```

4. Run the notebook from top to bottom.

5. Compare the generated outputs with the figures in:

   ```text
   analysis_outputs/figures/
   ```

The original data collection exports were obtained from the backend/server using the download routes listed in the **Data storage and export** section. For the final thesis analysis, the relevant exported data were stored locally and processed into the cleaned CSV files in:

```text
data/clean/
```

The final analysis does not require live access to the backend server.

To inspect the original raw export:

```text
data/rawdata/data tijdelijk.docx
```

To re-run or inspect the prototype, use the GitHub Pages link:

[https://mandydamsteegt.github.io/Master_Thesis/](https://mandydamsteegt.github.io/Master_Thesis/)

or open the local file:

```text
prototype/executable/index.html
```

---

## Data quality and exclusions

No participants were excluded from the final dataset.

The final sample consisted of **72 participants**, with **18 participants per condition**. Each participant completed **30 main trials**, resulting in **2160 trial-level observations**.

The final analysis reported in the thesis was conducted using:

```text
data/scripts/Data Analyse Defi (4).ipynb
```

The figures in `analysis_outputs/figures/` were generated from this final analysis notebook.

---

## Participant notes

Participant-level notes are stored in:

```text
misc/participant_notes.csv
```

The participant notes file records that no notable participant-level issues or irregularities were recorded during data collection.

---

## Important notes before running the prototype

Before using the prototype for real data collection, the following should be tested:

- all four experimental conditions
- speech playback
- audio check and secret word validation
- condition assignment
- data saving to the backend
- local JSON and CSV export
- source links in the verification panel
- complete participant flow from start to finish

---

## Limitations

This is a research prototype, not a production system.

Known limitations include:

- browser speech synthesis voices may differ between devices
- audio quality depends on participant hardware and browser settings
- local storage can be cleared by the browser or user
- the prototype cannot prevent participants from using external search tools
- speech playback may behave differently across browsers and operating systems
- online participation limits control over participants’ environment
- the evidence panel is a controlled research mechanism and does not represent a full real-world search process
- the backend uses prototype-level data storage and is not a production-grade data platform

---

## Privacy

The prototype is designed for anonymous academic data collection.

It does **not** ask for:

- participant name
- email address
- phone number
- direct personal identifiers

Data are stored with anonymous participant/session identifiers and are intended to be analysed at group level.

---

## Files not included

The following files or folders should not be included in this repository:

```text
node_modules/
.DS_Store
.env
```

The `node_modules/` folder can be recreated by running `npm install` inside the `ai_backhand_server/` folder. The `.DS_Store` file is a local macOS system file and is not needed for the project. Environment files should not be uploaded because they may contain private configuration values.

---

## Final note

The definitive analysis route for this thesis submission is:

```text
backend/server exports
→ local raw and structured exports
→ data/clean/
→ data/scripts/Data Analyse Defi (4).ipynb
→ analysis_outputs/figures/
```

The backend code is included for transparency about how data were collected and exported, but the final thesis analysis can be reproduced from the cleaned data and final analysis notebook included in this repository.
