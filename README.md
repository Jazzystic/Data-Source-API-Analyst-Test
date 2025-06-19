# Data Source API Analyst – Technical Assignment for Improvado

## Overview

This repository contains my solution to the technical assignment for the **Data Source API Analyst** role at **Improvado**. The objective of the assignment was to demonstrate the ability to interact with the GitHub REST API by performing authenticated requests, handling errors, interpreting responses, and documenting both the process and the outcome in a clear, structured format.

All implementation and testing were performed using Python in Google Colab.

---

## Repository Structure

├── Content/
│ ├── api_documentation.md # Full explanation of the endpoints tested and how they were used
│ ├── troubleshooting_guide.md # Notes on error handling and how issues were resolved
├── Postman_Collection/ # (Optional) For any exported test environments or notebooks
├── README.md # This file – general overview of the project


---

## Goals of the Assignment

- Authenticate to the GitHub API using a personal access token
- Search public repositories using a keyword
- Retrieve recent commits from a known repository
- Attempt to fetch a file from a repository and handle a 404 error properly
- Document the approach, encountered issues, and results in Markdown files

---

## Endpoints Covered

- `GET /search/repositories`
- `GET /repos/{owner}/{repo}/commits`
- `GET /repos/{owner}/{repo}/contents/{path}`

These were tested using real examples and interpreted programmatically.

---

## Documentation Included

- `api_documentation.md`: Describes each API call, expected behavior, parameters, and outputs
- `troubleshooting_guide.md`: Explains how errors (like 404) were handled and what decisions were made during testing

---

## Notes

- No credentials or tokens are included in this repository.
- All code was tested in a controlled environment and kept secure at runtime.
- The implementation avoids committing any sensitive information.

---

## Author

Julio César López Mendoza  
[GitHub profile](https://github.com/Jazzyctic)
