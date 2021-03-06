---
title: Workspace File
weight: 3
---

Workspace is configured by the means of a `workspace.yml` file.
This file does support go templates hence it is possible to create parameterized files using data objects.

There are serveral types of data objects:

- **Workspace data objects**: Variables which are defined on the workspace
- **Runtime data objects**: Variables that are initialized by the command-line runtime

{{< toc >}}

## Runtime data objects

A workspaces can be hierarchically composed with its parent workspaces files.

```plain
level-0/
├── .nitroci
|    └── workspace.yml
└── level-1
    ├── .nitroci
    |   └── workspace.yml
    ├── README.md
    ├── worksplace.yml
    └── level-2
        ├── .nitroci
        |   └── workspace.yml
        └── README.md
```

Considering the sample above we have would get the following:

- `level-0/workspace.yml`:  at this level there is no composition
- `level-0/level-1/workspace.yml`:  this file is composed with level-0/workspace.yml
- `level-0/level-1/level-2/workspace.yml`:  this file is composed with level-0/workspace.yml and level-1/workspace.yml

In the event of a configuration conflitct the value on the bottom workspace overrides the the top one.

Here a comprehensive list of the full runtime data objects.

| KEY                      | SAMPLE VALUE                       | DESCRIPTION                                                |
|--------------------------|------------------------------------|------------------------------------------------------------|
| Environment              | local                              | Current environment                                        |
| Workspace.Home           | ~/level-0/level-1/.nitroci         | Physical workspace path                                    |
| Virtual.Workspace.Home   | ~/level-0/level-1/level-2/.nitroci | Virtual workspace path                                     |

## Workspace sample file

Below an example of `workspace.yml`.

```yml
version: 1
workspace:
  id: 40b13d1a1c77457789daa0be89c33335
  name: my-project
  settings:
    encryption:
      key: {{ upper .Environment }}_ENCRYPTION_SECRET
    environments:
      variables:
        name:  PIPE_{{ upper .Context.Environment.Name }}
    pipelines:
      bitbucket:
        workspace: my-company
        slug: my-project
  plugins:
    - name: bitbucket
      version: 0.0.2
    - name: jfrog
      version: 0.0.2
  values:
    - PROJECT_NAME:
        value: my-project
environments:
  - name: dev
    encryption:
      paths:
        - .vscode
        - .postman/dev
        - {{ .Workspace.Home }}/.nitroci/environments/dev
commands:
  - name: provision
    description: Provision the environment
    steps:
      - scripts:
          - pyenv virtualenv 3.9.6 {{ .PROJECT_NAME }}-3.9.6 && pip install --upgrade pip
  - name: install
    description: Provision the environment
    steps:
      - scripts:
          - pip install -r ./requirements.txt
  - name: destroy
    description: Destroy the environment
    steps:
      - script: pyenv uninstall -f {{ .PROJECT_NAME }}-3.9.6
```
