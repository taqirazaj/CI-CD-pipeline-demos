# CI-CD-pipeline-demos
CI/CD Pipeline Demos: This repo showcases various CI/CD pipelines I created to demonstrate my skills. These pipelines are for illustrative purposes only and are not configured to run in a live environment. Explore to see my expertise in CI/CD setups!

# CI/CD Pipeline for Cypress Tests

This README provides instructions for setting up a CI/CD pipeline using GitHub Actions to run Cypress automated tests on a self-hosted runner.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Setting Up a Self-Hosted Runner](#setting-up-a-self-hosted-runner)
3. [Creating the GitHub Actions Workflow](#creating-the-github-actions-workflow)

## Prerequisites

1. **GitHub Repository**: Ensure you have a GitHub repository set up for your project.
2. **Self-Hosted Runner**: You need a self-hosted runner configured and registered with your GitHub repository.
3. **Cypress Setup**: Cypress should be installed in your project. Add it to your `package.json` dependencies.

## Setting Up a Self-Hosted Runner

1. **Create and Register a Self-Hosted Runner**:
   - Go to your GitHub repository.
   - Navigate to **Settings** > **Actions** > **Runners** > **Add runner**.
   - Follow the instructions to download and configure the runner for your operating system.

2. **Install Required Software**:
   - Ensure the runner machine has all necessary software installed, such as Node.js and npm.

3. **Run the Runner**:
   - Execute the provided command to start the runner. You can also configure it to run as a service.

4. **Verify**:
   - Check your GitHub repository’s **Actions** settings to ensure the runner is online.

## Creating the GitHub Actions Workflow

Create a file named `.github/workflows/cypress-tests.yml` in your repository with the following content:

```yaml
name: Cypress Tests

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  cypress:
    runs-on: self-hosted
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '20.x'

      - name: Install dependencies
        run: npm install

      - name: Run Cypress tests
        run: npm run cy:run
