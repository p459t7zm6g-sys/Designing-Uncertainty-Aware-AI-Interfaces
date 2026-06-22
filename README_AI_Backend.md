# AI Hedging Backend

This folder contains the backend service for the master thesis experiment prototype:

**Designing Uncertainty-Aware AI Interfaces: Verbal Hedging and Trust Calibration in Text and Synthetic Speech**

The backend was used during data collection to receive, store, and export experiment data submitted by the browser-based participant interface.

## Project purpose

The backend supports a browser-based experiment in which participants evaluate AI-generated answers. The study investigates how verbal hedging and output modality influence trust, verification behaviour, and reliance decisions.

The frontend experiment collects behavioural and questionnaire data. After a participant completes the experiment, the frontend sends the completed session data to this backend. The backend stores the submitted data as JSON files and provides export endpoints for later analysis.

## Main responsibilities

This backend is responsible for:

- receiving participant session data from the experiment page;
- storing submitted data as JSON files;
- providing export endpoints for collected experiment data;
- supporting participant-level data export;
- supporting trial-level data export;
- supporting qualitative reflection/interview response export;
- keeping backend data storage separate from the frontend prototype.

## Technology stack

The backend is built with:

- Node.js
- Express.js
- CORS
- JSON file storage

## Folder structure

```text
ai_backend_server/
├── README_AI_Backend.md
├── package.json
├── package-lock.json
└── server.js
```

When the backend is running and receives data, submitted sessions are stored in a local `data/` directory.

The `node_modules/` folder is not included in the GitHub repository. Dependencies can be installed locally with `npm install`.

## Main file

The main application logic is located in:

```text
server.js
```

This file defines the Express server, API routes, data-saving logic, and export functionality.

## Installation

To install the backend dependencies, run:

```bash
npm install
```

## Running locally

To start the backend locally, run:

```bash
node server.js
```

Or, if a start script is configured in `package.json`, run:

```bash
npm start
```

By default, the server uses the port defined by the environment variable `PORT`. If no port is provided, it falls back to the default port configured in the code.

## Data submission endpoint

The frontend sends completed participant session data to the backend endpoint configured in the experiment page.

Example frontend configuration:

```javascript
const WEBHOOK_URL = "https://ai-hedging-backend.onrender.com/api/experiment";
```

The backend receives a JSON payload containing:

- participant metadata;
- assigned experimental condition;
- questionnaire responses;
- computed questionnaire scores;
- trial-level behavioural logs;
- final reflection responses;
- session completion status.

## Stored data

Submitted experiment sessions are stored as JSON files.

Each saved file contains session-level metadata and trial-level logs.

The trial-level logs include:

- participant ID;
- condition;
- hedging condition;
- modality condition;
- item ID;
- block number;
- trial index;
- answer correctness;
- displayed AI answer;
- hedge phrase;
- hedge type;
- verification behaviour;
- evidence dwell time;
- source-opening behaviour;
- final accept/reject decision;
- decision time;
- final decision accuracy.

The session metadata includes:

- informed consent status;
- session start and end time;
- manipulation-check responses;
- trust questionnaire responses;
- NASA-TLX workload responses;
- User Experience Questionnaire responses and scores;
- post-task responses;
- final reflection answers;
- session completion status.

## Export functionality

The backend provides export routes for downloading collected data.

The export routes used during the thesis project were:

| Route | Purpose |
|---|---|
| `/api/download-all` | Full raw export of all participant sessions |
| `/api/download-participants-csv` | Participant-level CSV export |
| `/api/download-trials-csv` | Trial-level long-format CSV export |
| `/api/download-interviews-csv` | Qualitative reflection/interview response CSV export |

These exports were downloaded locally and used as the basis for the cleaned datasets in the main thesis repository.

The final cleaned datasets are stored in:

```text
data/clean/
```

in the main experiment repository.

## Data flow

The data collection and processing workflow was:

1. The participant completed the browser-based experiment.
2. The frontend sent the completed session to the backend.
3. The backend stored the submitted session as a JSON file.
4. The collected data were exported through the backend export routes.
5. The exported data were cleaned and transformed into participant-level, trial-level, and qualitative datasets.
6. The cleaned datasets were analysed in the final Jupyter notebook.

## Reproducibility

This backend documents how the data were collected and exported during the experiment.

The final thesis analysis does not require the backend server to be running. The final analysis can be reproduced from the cleaned CSV files and the final analysis notebook included in the main thesis repository.

The backend is therefore included for transparency about the data collection infrastructure, while the cleaned data and analysis notebook form the definitive reproduction route for the reported thesis results.

## Deployment

This backend can be deployed on a Node.js hosting platform such as Render.

Typical deployment steps are:

1. Push the backend folder or backend repository to GitHub.
2. Create a new Node.js web service on the hosting platform.
3. Connect the GitHub repository.
4. Set the build command to:

```bash
npm install
```

5. Set the start command to:

```bash
node server.js
```

6. Deploy the service.
7. Copy the deployed backend URL.
8. Use that URL as the `WEBHOOK_URL` in the frontend experiment page.

## Environment variables

The backend can use the following environment variable:

| Variable | Purpose |
|---|---|
| `PORT` | Determines which port the Express server listens on |

When deployed on platforms such as Render, the platform usually sets the `PORT` value automatically.

No private credentials, API keys, passwords, database connection strings, or secret environment variables are included in this repository.

## Important notes before data collection

Before using the backend for real participant data collection, the following should be tested:

- the backend starts successfully;
- the frontend can send data to the backend;
- submitted JSON files are saved correctly;
- participant-level export works;
- trial-level CSV export works;
- qualitative reflection/interview export works;
- incomplete sessions are handled correctly;
- completed sessions contain all expected metadata and logs;
- the hosting platform remains active during the data collection period.

## Privacy and data handling

The backend was designed for anonymous academic research data.

The frontend did not ask participants for direct personal identifiers such as:

- name;
- email address;
- phone number.

Data were stored using anonymous participant or session identifiers. The collected data were intended to be analysed and reported at group level.

## Limitations

This backend is a research prototype, not a production-grade data platform.

Known limitations include:

- data are stored as local JSON files;
- file-based storage may not be suitable for large-scale studies;
- hosting platforms may restart or pause inactive services;
- data persistence depends on the hosting provider configuration;
- no full user authentication is implemented;
- server-side validation is limited to prototype-level checks.

## Security note

This backend should not expose destructive routes publicly during real data collection.

Any endpoint that clears, deletes, or modifies stored data should be removed, disabled, or protected before deployment.

## Related frontend prototype

This backend was used together with the frontend experiment prototype in the main thesis repository.

The frontend contains the browser-based participant interface and is available through GitHub Pages.

The backend receives the completed session data from the frontend and provides the export routes used to prepare the final cleaned datasets for analysis.
