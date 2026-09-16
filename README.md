# Jenkins CI/CD Demo

A simple hands-on project to understand **Jenkins Pipeline as Code** and build a basic CI/CD workflow using Jenkins, Git, and GitHub.

## 🎯 What We Demonstrated

```text
GitHub Repository
       ↓
Jenkins
       ↓
Checkout
       ↓
Build
       ↓
Test
       ↓
Deploy
```

### Jenkins concepts covered

* Jenkins Controller and Executor
* Jenkins Pipeline
* **Jenkinsfile** (Pipeline as Code)
* Declarative Pipeline
* `agent`
* `environment`
* `stages` / `stage`
* `steps`
* `sh`
* `when`
* `post`
* SCM checkout using `checkout scm`
* Jenkins Pipeline connected to a GitHub repository

## 📁 Project Structure

```text
jenkins-demo/
├── app/
│   └── app.sh
├── tests/
│   └── test.sh
├── Jenkinsfile
├── README.md
└── .gitignore
```

## 🔧 Application & Test

The application is a simple shell script:

```bash
./app/app.sh
```

The test script validates the application's output:

```bash
./tests/test.sh
```

Exit codes are used to communicate the result:

```text
0       → Success
non-zero → Failure
```

This allows Jenkins to determine whether a shell step passed or failed.

## 🚀 Jenkins Pipeline

The `Jenkinsfile` defines the CI/CD workflow:

```text
Checkout → Build → Test → Deploy
```

* **Checkout** → Gets source code from GitHub
* **Build** → Runs the application build command
* **Test** → Executes automated tests
* **Deploy** → Runs only for the `main` branch
* **Post** → Reports pipeline success/failure

## 🔗 Jenkins + GitHub Configuration

Jenkins was configured to:

```text
Repository → GitHub jenkins-demo
Branch     → main
Script     → Jenkinsfile
```

The pipeline was initially triggered manually using:

```text
Jenkins → Build Now
```

Jenkins then:

```text
1. Checks out the repository
2. Reads the Jenkinsfile
3. Executes the pipeline stages
4. Displays the result in Stage View
5. Provides detailed logs in Console Output
```

## 🧪 Local Setup

Run the application:

```bash
./app/app.sh
```

Run tests:

```bash
./tests/test.sh
```

Initialize and push the project:

```bash
git init
git add .
git commit -m "Initial Jenkins CI/CD demo"
git branch -M main
git remote add origin <GITHUB_REPOSITORY_URL>
git push -u origin main
```

## 🧠 Key Takeaway

> **Jenkinsfile defines WHAT Jenkins should do; a trigger determines WHEN Jenkins should do it.**

This project establishes the foundation for the next step: **automatically triggering Jenkins through a GitHub webhook instead of using `Build Now`.**
