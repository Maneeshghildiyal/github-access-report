🚀 GitHub Access Report System

A high-performance Spring Boot backend service that integrates with the GitHub REST API to generate organization-level access reports. It maps users to repositories they can access using asynchronous and parallel processing (WebFlux + CompletableFuture), making it efficient for large-scale organizations.

✨ Key Highlights

⚡ Parallel data fetching for high performance
🔄 Non-blocking API calls using WebClient
📊 Supports 100+ repositories and 1000+ users
🧠 Caching with Caffeine to reduce API calls
🛡️ Proper error handling (401, 403, 404)
📦 Clean and structured JSON response

🛠️ Tech Stack

Java 17 • Spring Boot • WebFlux • CompletableFuture • Caffeine Cache • Maven

⚙️ Setup & Run
Install Java 17+
Create GitHub Personal Access Token (repo, read:org)
Update application.yml

github:
  token: ${GITHUB_TOKEN}
  org: your-org-name

Set environment variable

export GITHUB_TOKEN=your_token_here

Run

mvn clean install
mvn spring-boot:run

Server runs at: http://localhost:8080

📡 API

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

🎯 Why This Project

This project demonstrates scalable backend development using parallel processing, API integration, caching, and clean architecture, making it suitable for real-world production scenarios.
