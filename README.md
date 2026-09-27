# Projektarebete Repository

The submitted project is located in the [Projekt](Projekt/) folder. See the [main project README](Projekt/README.md) for the goal, method, workflow, limitations, and assignment documentation.

## Repository Structure

```text
Projektarebete/                 # local repository and workspace
├── README.md                   # repository overview
├── Projekt/                    # submitted project
│   ├── main.ipynb              # step-by-step Jupyter Notebook
│   ├── keywords.json           # classifier keyword data
│   ├── README.md               # main project documentation
│   └── images/
│       └── workflow.pdf
└── venv/                       # local environment, excluded from GitHub
```

`venv/` is used only to run the project locally. It is not part of the submitted project or GitHub repository.

## Project Workflow

The project workflow is shown below. The diagram illustrates input validation, keyword loading, API search, filtering, and result display.

[View the construction architecture job-search workflow (PDF)](Projekt/images/workflow.pdf)
