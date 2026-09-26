# Prototype Job Search for Construction Architecture Roles

GitHub repository: [github.com/karlakardos/Projektarebete](https://github.com/karlakardos/Projektarebete)

## Goal

This project is a prototype for finding construction and architecture-related jobs through the JobTech API. The user enters one or two keywords, such as `arkitekt`, `revit`, `bim`, or `projektering`. The program searches the API, excludes advertisements classified by its keyword rules as IT-related, and prints the remaining construction/architecture results.

The project is intentionally limited. It demonstrates basic Python, API use, data handling, functions, loops, conditions, classes, inheritance, and error handling without attempting to create a complete job-search system.

[View the construction architecture job-search workflow (PDF)](images/workflow.pdf)

The diagram shows the intended search stages and is a conceptual overview of the implementation.

## Method

1. Read one or two keywords from the user.
2. Normalize the input by removing extra spaces, converting it to lowercase, and splitting it into a list.
3. Check that the input contains an architect role or construction/architecture keyword.
4. Request a limited number of advertisements from the JobTech API.
5. Clean the raw API records into simpler dictionaries.
6. Exclude job text containing an IT keyword and keep construction/architecture matches.
7. Print the matching headline, employer, city, and application link.

API endpoint:

```text
https://jobsearch.api.jobtechdev.se/search
```

The classifier checks complete words in job text. This prevents `it` from being found inside `revit`. The IT keyword set is retained only as an exclusion rule for the construction-focused search.

## Project Structure

```text
Projektarebete/
├── main.ipynb
├── keywords.json
├── images/
│   └── workflow.pdf
└── README.md
```

- `main.ipynb`: one step-by-step notebook containing imports, classes, classifier functions, API handling, output functions, and the main workflow.
- `keywords.json`: contains the IT, architecture, and role keyword sets.

## OOP And Error Handling

The project uses a parent class and a child class:

```python
Job
└── ArchitectureJob
```

`ArchitectureJob` inherits from `Job` and provides the category `bygg/arkitektur` through `get_category()`.

`try/except` is used around the API request to handle network errors, HTTP errors, invalid JSON, and unexpected API data. Input length is checked with ordinary `if` statements.

## Results And Risks

The API may return more jobs than the program displays after local filtering. For example, 9 jobs may be received while only 3 pass the local conditions.

The API data is external and may be broad or inconsistently categorized. Employers or the source system may classify jobs such as `Agile Architect` or `Solution Architect` in ways that do not match the intended construction field. The program cannot control the original categories or indexing.

The local classifier uses simple keyword matching and cannot fully understand context, synonyms, or the complete meaning of an advertisement. The result is therefore a keyword-based prototype, not a guarantee that every displayed job is perfectly relevant.

## Current Limitations

- The program accepts only one or two search words.
- The API may return partly relevant jobs.
- Local filtering may remove relevant jobs or retain jobs with imperfect categories.
- Results may change as the API data changes.
- The program does not rank results by relevance.
- `keywords.json` is the submitted JSON data file used by the classifier. Job advertisements are retrieved live from the API and are not stored permanently by the program.
- The search is focused on construction and architecture jobs, not IT architecture jobs.

## Running The Project

1. Open the project folder in VS Code.
2. Open `main.ipynb`.
3. Select a Python environment with `requests` installed.
4. Run the notebook cells in order.
5. Run the final cell to start the program.
6. Enter an architect role or construction/projection keyword, for example `arkitekt`, `revit`, `bim`, or `projektering`.

An internet connection is required because the program uses the JobTech API.

## Assignment Checklist

Already demonstrated by the current code:

- Python variables, lists, dictionaries, conditions, loops, and functions
- a parent class and child class using inheritance
- standard Python features and the external `requests` library
- public API data
- `try/except` handling for API errors
- Jupyter Notebook code

Still required or to be checked before submission:

- Include `keywords.json` as the project JSON data file.
- Add an analysis of AI-industry roles and trends.
- Add relevant professional certificates, such as AWS, Azure, or Databricks.
- Add a reflection on technical choices, results, difficulties, and improvements.
- Add the final GitHub repository link.
- Confirm at least five GitHub commits with clear messages.

## Reflection

The prototype shows that an external job API can be combined with keyword classification and object-oriented Python. The main difficulty is the quality and categorization of external job data. A future version could save API results, use more occupation fields, improve relevance filtering, and support more keywords. The current version keeps the logic understandable and focuses on construction-related architecture roles.

## GitHub

Repository link: **to be added before submission**
