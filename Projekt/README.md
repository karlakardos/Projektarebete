# Prototype Job Search for Construction Architecture Roles

GitHub repository: [github.com/karlakardos/Projektarebete](https://github.com/karlakardos/Projektarebete)

## Goal

This project is a prototype for finding construction and architecture-related jobs through the JobTech API. The user enters one or two keywords, such as `arkitekt`, `revit`, `bim`, or `projektering`. The program searches the API, excludes advertisements classified by its keyword rules as `exclude`, and prints the remaining construction/architecture results.

The project is intentionally limited. It demonstrates basic Python, API use, data handling, functions, loops, conditions, classes, inheritance, and error handling without attempting to create a complete job-search system.

[View the construction architecture job-search workflow (PDF)](images/workflow.pdf)

The diagram shows the intended search stages and is a conceptual overview of the implementation.

## Method

1. Read one or two keywords from the user.
2. Normalize the input by removing extra spaces, converting it to lowercase, and splitting it into a list.
3. Check that the input contains an architect role and/or construction/architecture keyword.
4. Request a limited number of advertisements from the JobTech API.
5. Clean the raw API records into simpler dictionaries.
6. Exclude job text containing an exclusion keyword and keep construction/architecture matches.
7. Print the matching headline, employer, city, and application link.

API endpoint:

```text
https://jobsearch.api.jobtechdev.se/search
```

The classifier checks complete words in job text. The `exclude` keyword set is used to remove unrelated advertisements from the construction-focused search.

## Project Structure

```text
Projektarebete/
├── REPOSITORY_OVERVIEW.md       # repository overview
├── Projekt/                     # submitted project
│   ├── main.ipynb
│   ├── keywords.json
│   ├── requirements.txt
│   ├── README.md
│   └── images/
│       └── workflow.pdf
└── venv/                        # local environment, excluded from GitHub
```

- `main.ipynb`: one step-by-step notebook containing imports, classes, classifier functions, API handling, output functions, and the main workflow.
- `keywords.json`: contains the architecture, exclusion, and role keyword sets.
- `requirements.txt`: lists the packages needed to run the notebook.
- `images/workflow.pdf`: project workflow diagram.
- `REPOSITORY_OVERVIEW.md`: short overview of the outer repository.
- `venv/`: local Python environment; excluded from GitHub.

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
3. Create or select a Python environment.
4. Install the required packages:

	```text
	pip install -r requirements.txt
	```

5. Run the notebook cells in order.
6. Run the final cell to start the program.
7. Enter an architect role and/or construction/projection keyword, for example `arkitekt`, `revit`, `bim`, or `projektering`.

An internet connection is required because the program uses the JobTech API.

## AI Industry And Role Analysis

This project demonstrates a small version of this type of work: it collects external job data, structures it, applies keyword-based analysis, and presents useful results to a user. The result is not an AI model, but it shows basic data processing that could later be expanded with better classification or machine learning.

## Relevant Professional Certificates

Relevant certificates for a future development of this project include:

- AWS Certified Cloud Practitioner or an AWS machine-learning certification
- Microsoft Azure Fundamentals or Azure AI Engineer Associate
- Databricks certifications related to data engineering or machine learning

These certificates are relevant because AI developers commonly work with cloud platforms, data pipelines, model services, and deployment environments. They are not required to run this prototype, but they are relevant to the professional context of the project.

## Reflection

The prototype shows that an external job API can be combined with keyword classification and object-oriented Python. The main difficulty is the quality and categorization of external job data. Employers and the source system may use broad or inconsistent categories, so the local filter cannot guarantee perfect results.

The construction-focused scope was chosen to make the problem understandable and useful for architects. Keeping the keyword groups in `keywords.json` makes them easier to update without changing the classifier code.

A future version could use more occupation fields, improve relevance filtering, support more keywords, save API results, and use a more advanced classification method. The current version prioritizes a simple, explainable prototype. Machine learning can help with analysis of the available jobs and provide more appropriate results.

## GitHub

Repository link: [github.com/karlakardos/Projektarebete](https://github.com/karlakardos/Projektarebete)

The project is version-controlled with GitHub and the repository history contains more than five commits with descriptive messages.
