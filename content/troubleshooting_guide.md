# Troubleshooting Guide – Data Source API Analyst assigment

This guide documents the technical issues I encountered while interacting with the GitHub REST API during this assignment. It also outlines how each issue was identified and resolved.

---

## Issue 1 – 404 Not Found (Missing File in Repository)

### Description:
When I initially attempted to retrieve the `README.md` file from the `octocat/Hello-World` repository using the `/contents/{path}` endpoint, the API returned a 404 Not Found error.

### Status Code:
Status code: 404


### API Call Example:
GET https://api.github.com/repos/octocat/Hello-World/contents/README.md


### Diagnosis:
The 404 response indicated that the file path did not exist. I verified manually that the repository does not include a `README.md` file at the root level.

### Resolution:
I repeated the test using a repository known to include the file:
GET https://api.github.com/repos/torvalds/linux/contents/README


The request returned a `200 OK` response with the expected file metadata, confirming the path and endpoint were functioning correctly.
## Notes on Rate Limiting

Although I did not encounter a `403 Rate Limit Exceeded` error, I was aware of the unauthenticated request limit of 60 requests per hour. I ensured that testing stayed well below this threshold.

---

## Summary

| Issue Code | Description        | Resolution Summary                      |
|------------|--------------------|-----------------------------------------|
| 404        | File not found     | Verified path; used a valid repository  |

All requests were reviewed for correctness, and any unexpected behavior was diagnosed through HTTP status codes and corrected by selecting appropriate repositories and paths.

