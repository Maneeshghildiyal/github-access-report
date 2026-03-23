🚀 GitHub Access Report System

A scalable Spring Boot backend service that connects to the GitHub REST API and generates an access report for an organization. The system retrieves repositories and their collaborators, then aggregates the data to show which users have access to which repositories.

📌 Project Overview

This application is built to provide visibility into repository access within a GitHub organization. Since organizations can contain hundreds of repositories and thousands of users, fetching this data sequentially is inefficient and slow.

To address this, the system uses asynchronous and non-blocking techniques with Spring WebFlux (WebClient) and CompletableFuture to fetch data in parallel. This significantly reduces response time and allows the service to scale efficiently.

✨ Key Features
Non-blocking API Calls
Uses WebClient to perform asynchronous HTTP requests to the GitHub API.
Parallel Data Fetching
Uses CompletableFuture to fetch repository and collaborator data concurrently.
Pagination Handling
Supports GitHub API pagination using per_page=100 to retrieve complete datasets.
Caching Support
Integrates Caffeine caching to reduce repeated API calls and avoid hitting rate limits.
Centralized Error Handling
Handles common errors such as authentication failures (401), rate limits (403), and invalid organizations (404) with clean responses.
🛠️ Tech Stack
Language: Java 17
Framework: Spring Boot
Web: Spring WebFlux (WebClient)
Concurrency: CompletableFuture, ConcurrentHashMap
Caching: Caffeine
Testing: JUnit 5, Mockito
Build Tool: Maven
⚙️ Setup Instructions
1. Prerequisites
Java 17 or above
GitHub Personal Access Token (PAT)
Required scopes: repo, read:org
2. Configuration

Update your application.yml file:

github:
  token: ${GITHUB_TOKEN}
  org: your-org-name

👉 Set your token as an environment variable:

export GITHUB_TOKEN=your_token_here
▶️ Run the Application
mvn clean install
mvn spring-boot:run

The application will start on:

http://localhost:8080
📡 API Endpoint
Get Access Report
GET /access-report
📊 Sample Response
{
  "organization": "example-org",
  "users": [
    {
      "username": "octocat",
      "repositories": [
        {
          "name": "Hello-World",
          "access": "ADMIN"
        }
      ]
    }
  ]
}
🧠 Design Decisions
Used parallel processing to handle large-scale data efficiently
Applied caching to reduce API load and improve performance
Structured response data for better readability and usability
Implemented layered architecture for maintainability
⚠️ Assumptions
The provided GitHub token has sufficient permissions
The organization exists and is accessible
API rate limits are handled through caching and optimized calls
📌 Summary

This project demonstrates how to build a scalable backend system that efficiently integrates with external APIs, handles large datasets, and provides meaningful aggregated insights through a clean REST interface.
