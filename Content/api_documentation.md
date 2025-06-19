# GitHub API Documentation – Data Source API Analyst Homework

## Overview

This document outlines the GitHub REST API endpoints I used to fulfill the assignment requirements: searching for public repositories, retrieving commits, and accessing file content. Each endpoint was tested using Google Colab, and all requests were authenticated using a personal access token. I implemented and verified each use case successfully.

---

## Authentication

All requests were authenticated using a GitHub personal access token (PAT) passed via the `Authorization` header.

### Headers used:
Authorization: Bearer YOUR_TOKEN_HERE
X-GitHub-Api-Version: 2022-11-28

I manually added the token to the notebook at runtime. The token was not committed to the repository for security reasons.

---

## 1. Search Public Repositories

### Endpoint:
GET https://api.github.com/search/repositories


### Example:
https://api.github.com/search/repositories?q=data+in:name&per_page=5


### Parameters:
- `q`: Query string (e.g., `"data"`)
- `per_page`: Number of results per page (default: 30, max: 100)
- `page`: Page number for pagination
- `sort`, `order`: Optional sorting criteria

### Result:
The request returned a `200 OK` response and a list of repositories. I confirmed the request worked by checking that the `items` array contained valid repository metadata.

---

## 2. Get Commits from a Repository

### Endpoint:
GET /repos/{owner}/{repo}/commits


### Example:
https://api.github.com/repos/torvalds/linux/commits


### Parameters:
- `sha`: Commit SHA or branch (optional)
- `author`: GitHub username to filter by author
- `since`, `until`: Filter commits by date range
- `per_page`, `page`: Pagination

### Result:
I tested this endpoint using the repository `torvalds/linux`. The response returned a `200 OK` status and a list of recent commits, including commit messages, SHA values, and author details. This validated the endpoint and the authentication setup.

---

## 3. Get File Content from a Repository

### Endpoint:
GET /repos/{owner}/{repo}/contents/{path}


### Example:
https://api.github.com/repos/torvalds/linux/contents/README


### Notes:
- The `path` must be valid and point to an existing file.
- The `content` is returned base64-encoded.

### Handling a 404 Error:

When I initially tested the `octocat/Hello-World` repository, the API returned a 404 Not Found response. This was expected, since the repository does not contain a README file at the root level.

To validate the functionality of the endpoint, I repeated the request using the `torvalds/linux` repository, which is known to contain a `README` file. This second attempt returned a 200 OK response, confirming that my authentication headers and request structure were implemented correctly.

---

## Rate Limits

| Authentication | Requests per hour |
|----------------|-------------------|
| None           | 60                |
| With token     | 5,000             |

I ensured that all requests were made with a token to avoid hitting the unauthenticated rate limit.

---

## Error Handling

| Code | Meaning              | Strategy                                 |
|------|----------------------|------------------------------------------|
| 401  | Unauthorized         | Verified token was copied correctly      |
| 403  | Rate limit exceeded  | Ensured authentication via token         |
| 404  | Not found            | Checked file paths or repository details |

All errors were handled manually during testing by inspecting status codes and adapting parameters as needed.

---

## Conclusion

All three API endpoints were tested and validated in a secure and authenticated environment using Google Colab. 
The tests confirmed correct usage of authentication headers, error handling, and pagination where applicable. 
All findings are based on actual test runs conducted during the assignment.
