## Why Newman

- Newman is the command-line runner for Postman collections.
- Useful for automation and CI/CD (e.g., Jenkins), and for reporting.

## Install (prereq)

- **What is Node.js?**
    - Node.js lets you run **JavaScript** programs on your computer (outside the browser).
    - Newman is built and distributed as a JavaScript tool, so Node.js is the runtime it needs.
- **What is npm? (Why do we need it?)**
    - **npm** = *Node Package Manager*.
    - It’s the easiest way to **download and install** Node-based tools.
    - We use npm to install Newman (and extra reporters) in a reliable, repeatable way.
- Install **Node.js** (it includes **npm**).
- Install Newman via npm (Newman is a JS package).

## Export files before running

- Export the **collection** JSON.
- Export the **environment** JSON (and globals if used).

## Run from CLI

- Basic:
    - `newman run <collection.json> -e <environment.json>`
- If you use globals:
    - `newman run <collection.json> -e <environment.json> -g <globals.json>`

## Windows tip

- Use **Git Bash** if you want a Linux-like CLI experience / commands on Windows.

## Reporting

- Newman can generate reports.
- HTML (basic): `-r html` (can combine with CLI, e.g. `-r cli,html`)
- Better HTML: install `newman-reporter-htmlextra`, then run with `-r htmlextra`

*Why install a reporter?*

- Newman supports different “reporters” (output formats).
- The default console output is useful, but HTML reports are easier to read/share.
- `htmlextra` adds a more detailed, nicer-looking HTML report.

## Data-driven runs

- Supply data file:
    - `-d <testdata.csv|testdata.json>`

## Iterations

- Run N iterations:
    - `-n 5`

## Notes

- Newman execution is generally faster than the Postman Collection Runner UI.
