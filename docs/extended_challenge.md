# Extended Challenge: From Debugging to Production Engineering

The original seven labs teach you how to investigate bugs in a Django application. This extension challenges you to take the same application beyond local development and demonstrate the engineering practices used to build, secure, deploy and operate a reliable service.

This is an **optional extension**, not a replacement for the original tutorial. Complete the original labs first. Keep their learning environment intact and make your production-engineering changes in a separate branch.

## The mission

Act as the engineer responsible for taking this Django application from a developer's laptop to a service that can be tested, packaged, deployed and supported.

You are not expected to implement every technology at once. Work through the stages below, record your decisions, and provide evidence that each stage works.

## Challenge stages

### 1. Establish a reproducible development environment

- Run the project in WSL/Linux using a Python virtual environment.
- Record the Python version and dependency installation steps.
- Move configuration into environment variables; do not commit real credentials or production secrets.
- Add or improve a concise developer setup guide.
- Confirm the original Django tests still pass.

**Evidence:** setup instructions, dependency list, test output and a redacted example environment file.

### 2. Containerise the application

- Create a Dockerfile for the Django application.
- Add a Docker Compose configuration for the application and a database such as PostgreSQL.
- Use environment variables for configuration and provide persistent database storage.
- Add a health check and document how to start, stop and inspect the services.
- Run database migrations in a documented, repeatable way.

**Evidence:** Dockerfile, Compose file, successful startup instructions and service health-check results.

### 3. Build a continuous integration pipeline

Use GitHub Actions to run checks on pull requests and pushes:

- Install dependencies.
- Run Django tests.
- Run Ruff linting and formatting checks.
- Run a dependency or vulnerability scan.
- Fail the workflow when a required check fails.

**Evidence:** workflow YAML, a passing workflow run and an example of a deliberately failing check.

### 4. Apply application-security basics

- Review Django settings for debug mode, allowed hosts, secure cookies and secret handling.
- Check that secrets are not committed to Git.
- Add dependency vulnerability checking.
- Document the application's authentication and permission boundaries.
- Record security findings and explain which are fixed, accepted or deferred.

**Evidence:** security checklist, scan output and a short findings log. Do not publish real secrets or sensitive test data.

### 5. Add operational visibility

- Use structured application logging.
- Ensure errors include enough context to investigate without logging passwords, tokens or personal data.
- Add a health endpoint or documented health-check mechanism.
- Define a small set of useful signals, such as request failures, response latency and application availability.
- Write a sample incident report with symptoms, timeline, root cause, resolution and prevention.

**Evidence:** example redacted logs, health-check result, monitoring design and incident report.

### 6. Deploy to a cloud environment (optional)

Choose one cloud platform: AWS, Azure or OCI.

- Document the architecture and network exposure.
- Deploy a test instance using a low-cost or free-tier approach where eligible.
- Store secrets outside source control.
- Restrict administrative access and avoid exposing the database publicly.
- Document deployment, rollback, backup and teardown steps.
- Set a spending limit or budget alert before creating chargeable resources.

**Evidence:** architecture diagram, deployment instructions and redacted proof of a successful deployment. Never include credentials, public admin URLs containing tokens, or sensitive infrastructure details.

### 7. Infrastructure as code (advanced)

- Describe the required cloud resources using Terraform.
- Separate configuration from secrets.
- Validate and format the configuration.
- Explain the plan before applying it.
- Document how to destroy the test environment and avoid leaving billable resources running.

**Evidence:** Terraform configuration, validation output and a reviewed plan. A live apply is optional.

## Definition of done

The extension is complete when you can demonstrate that:

- [ ] The original seven debugging labs remain usable.
- [ ] Another developer can reproduce the local environment from your instructions.
- [ ] The application can be built and started in containers.
- [ ] Automated tests and quality checks run in GitHub Actions.
- [ ] Security checks and secret-handling practices are documented.
- [ ] Logs and health checks support a basic troubleshooting exercise.
- [ ] At least one incident report explains a fault from detection through prevention.
- [ ] Cloud deployment and Terraform are documented if you chose those optional stages.

## Suggested deliverables

Keep the extension organised and reviewable. A possible structure is:

```text
docs/
  extended_challenge.md
  operations/
    incident-report-template.md
    security-checklist.md
    deployment-runbook.md
  architecture/
    deployment-overview.md
Dockerfile
compose.yaml
.github/
  workflows/
    ci.yml
```

Adapt this structure to the repository rather than creating empty files just to match the example.

## Constraints and good engineering practice

- Preserve the original tutorial and its Git history.
- Make incremental changes and explain why each dependency is needed.
- Prefer local testing before cloud deployment.
- Do not commit secrets, real customer data or unredacted logs.
- Do not assume a free tier is cost-free in every region or account. Check current pricing and tear down resources after testing.
- Kubernetes is deliberately not a requirement. Learn containers, CI, security and operational fundamentals first; add orchestration only if there is a clear learning objective.

## What this challenge demonstrates

Completing the extension can provide evidence of practical skills in Python/Django, Linux/WSL, Docker, automated testing, GitHub Actions, application security, observability, incident response and, in the optional stages, cloud infrastructure and Terraform.

The goal is not to collect tools. The goal is to show that you can diagnose a defect, make a controlled change, verify it, deploy it safely and explain how you would operate the result.
