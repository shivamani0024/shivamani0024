# Hi, I'm Shivamani

### Computer Science Engineering Student | Full-Stack Developer | Problem Solver

I'm a **B.Tech CSE student at Mahatma Gandhi Institute of Technology (MGIT)**, currently building my skills in software development, backend systems, and problem solving.

I enjoy turning ideas into practical projects and continuously learning new technologies.

---

## About Me

* Currently pursuing **B.Tech in Computer Science & Engineering**
* Interested in **Full-Stack Development, Backend Development & Software Engineering**
* Learning and practicing **Java, Python, JavaScript and SQL**
* Building projects with **Node.js, Express.js, MySQL and REST APIs**
* Practicing **Data Structures & Algorithms**
* Exploring **AI/ML and modern software development**
* Interested in building projects that solve real-world problems

---

## Tech Stack

### Languages

`Java` `Python` `JavaScript` `HTML` `CSS` `SQL`

### Backend & Frameworks

`Node.js` `Express.js` `REST APIs`

### Databases

`MySQL` 

### Tools

`Git` `GitHub` `VS Code` `Android Studio`

---

## Featured Project

### Coding Performance Tracker

A full-stack platform for tracking and comparing coding performance across competitive programming platforms.

**Features:**

* Student registration and authentication
* Coding profile management
* LeetCode, CodeChef, Codeforces and HackerRank statistics
* Student search
* Performance dashboard
* Leaderboard
* Admin-based statistics updates

**Tech:** Node.js · Express.js · MySQL · JavaScript · REST APIs · JWT

---

## Currently Learning

* Data Structures & Algorithms
* Advanced Java
* Backend Development
* Database Design
* System Design Fundamentals
* AI/ML
* Cloud & Deployment

---

## Goals

My goal is to become a strong **software engineer** by building real-world projects, improving my problem-solving skills, and gaining a deep understanding of computer science fundamentals.

---

## Connect With Me

* Email: shivamani0024@gmail.com


---

### "Build. Learn. Improve. Repeat."



.
Jenkins Pipeline Project Tasks - Step by Step
Solutions
Task 1: Simple Echo Pipeline
1. Create a new pipeline job in Jenkins named **EchoPipeline**.
2. Use the following Declarative pipeline script:
```
pipeline {
agent any
stages {
stage('Echo') {
steps {
echo 'Hello, Jenkins Pipeline!'
}
}
}
}
```
3. Run the job → Check console output → You should see `Hello, Jenkins Pipeline!`.
Task 2: Multi-Stage Pipeline
1. Create a pipeline job called **BuildTestPipeline**.
2. Use the following script:
```
pipeline {
agent any
stages {
stage('Build') {
steps { echo 'Building the project...' }
}
stage('Test') {
steps { echo 'Running tests...' }
}
stage('Deploy') {
steps { echo 'Deploying application...' }
}
}
}
```
3. Run the job → Stage view will show Build, Test, and Deploy stages.
Task 3: Workspace File Handling
1. Create a pipeline job called **FilePipeline**.
2. Script:
```
pipeline {
agent any
stages {
stage('Create File') {
steps {
writeFile file: 'pipeline.txt', text: 'Created by Jenkins Pipeline'
}
}
stage('Show File') {
steps {
powershell 'Get-Content pipeline.txt' // use 'cat' for Linux
}
}
}
}
```
3. Run job → Console output will display file content.
Task 4: Parameterized Pipeline
1. Create a pipeline job called **UserPipeline**.
2. Add a **String Parameter** named `USERNAME`.
3. Script:
```
pipeline {
agent any
parameters {
string(name: 'USERNAME', defaultValue: 'User', description: 'Enter your name')
}
stages {
stage('Greet') {
steps {
echo "Hello, ${params.USERNAME}!"
}
}
}
}
```
4. Run builds with different USERNAME values.
Task 5: Scheduled Pipeline
1. Create a job called **ScheduledPipeline**.
2. Configure build triggers → Add `H/5 * * * *` (every 5 minutes).
3. Script:
```
pipeline {
agent any
triggers {
cron('H/5 * * * *')
}
stages {

stage('Show Time') {
steps {
powershell 'Get-Date' // use 'date' for Linux
}
}
}
}
```
4. Jenkins will trigger the job automatically every 5 minutes.
Task 6: Git-Integrated Pipeline
1. Create a job called **GitPipeline**.
2. Configure it with your GitHub repo URL.
3. Script:
```
pipeline {
agent any
stages {
stage('Checkout') {
steps {
git branch: 'main', url: 'https://github.com/your-repo.git'
}
}
stage('Build') {
steps {
echo 'Compiling code...'
}
}
stage('Commit Info') {
steps {
powershell 'git log -1 --pretty=%B' // use 'sh' on Linux
}
}
}
}
```
4. Run → Jenkins will pull code, simulate build, and show last commit message.
Jenkins Freestyle Project Setup Guide
Step 1: Open Jenkins
• Launch a browser, and go to Jenkins (http://localhost:8080) if running locally.
• Login with your credentials.
Step 2: Create a New Freestyle Project
• Click 'New Item' on the dashboard.
• Enter a name for the project, e.g., BranchTaskProject.
• Select Freestyle project.
• Click OK.
Step 3: Configure the Project
• Scroll down to the Build section.
• Click 'Add build step' → Execute Windows batch command.
• Paste the following batch code:
@echo off
setlocal enabledelayedexpansion
echo ==============================
echo Jenkins Test Script
echo ==============================
:: Ensure WORKSPACE variable is set
if "%WORKSPACE%"=="" (
 echo ERROR: WORKSPACE environment variable is not defined.
 exit /b 1
)
echo Workspace folder is: "%WORKSPACE%"
:: List all files in workspace (ignore errors if empty)
dir "%WORKSPACE%" 2>nul
echo.
echo Creating target folder...
set TARGET_DIR="C:\inetpub\wwwroot\Devops"
:: Create target folder if it doesn't exist
if not exist %TARGET_DIR% (
 mkdir %TARGET_DIR%
 if errorlevel 1 (
 echo ERROR: Failed to create target folder %TARGET_DIR%
 exit /b 1
 )
)
echo.
echo Creating sample file...

set SAMPLE_FILE="%WORKSPACE%\test.txt"
echo Hello from Jenkins > %SAMPLE_FILE%
if not exist %SAMPLE_FILE% (
 echo ERROR: Failed to create sample file %SAMPLE_FILE%
 exit /b 1
)
echo.
echo Copying sample file to target folder...
copy %SAMPLE_FILE% %TARGET_DIR% >nul
if errorlevel 1 (
 echo ERROR: Failed to copy file to %TARGET_DIR%
 exit /b 1
)
echo.
echo ==============================
echo Test Completed Successfully
echo ==============================
endlocal
Step 4: Save the Job
• Scroll down and click Save.
Step 5: Run the Job
• Open the project page.
• Click 'Build Now' on the Build History panel.
• Click the build number and then Console Output to view logs.
• The batch script will create a folder at C:\inetpub\wwwroot\Devops, create a test.txt in the
workspace, copy it to the folder, and display success messages.
Jenkins Freestyle Project - Practical Tasks
Task 1: Create a Simple Hello World Project
• Create a new Freestyle project called HelloWorldJob.
• Add a Windows batch command or Shell command (Linux) to print 'Hello, Jenkins!'.
• Run the job and check the Console Output.
Solution:
Windows:
echo Hello, Jenkins!
Linux:
echo "Hello, Jenkins!"
Task 2: Use Workspace Variable
• Create a project called WorkspaceJob.
• Add a build step that prints the WORKSPACE environment variable.
• Verify in the console output that the path to the workspace is correct.
Solution:
Windows:
echo The workspace path is: %WORKSPACE%
Linux:
echo "The workspace path is: $WORKSPACE"
Task 3: File Creation and Copy
• Create a project FileCopyJob.
• Add a batch command that creates a file test.txt in the workspace and copies it to a folder.
• Verify the file is copied.
Solution:
Windows:
echo Hello from Jenkins > %WORKSPACE%\test.txt
copy %WORKSPACE%\test.txt C:\inetpub\wwwroot\Devops\
Linux:
echo "Hello from Jenkins" > $WORKSPACE/test.txt
cp $WORKSPACE/test.txt /var/www/devops/
Task 4: Parameterized Build
• Create a project ParameterizedJob.
• Add a String Parameter called USERNAME.
• In the build step, print Hello, $USERNAME.
• Build the job multiple times with different values and check the output.
Solution:
Windo
echo Hello, %USERNAME%
Linux:
echo "Hello, $USERNAME"
Task 5: Schedule Builds
• Create a project ScheduledJob.
• Configure it to run every 2 minutes (H/2 * * * *).
• In the build step, echo the current date and time.
• Verify multiple builds are triggered automatically.
Solution:
Windows:
echo Current date and time: %date% %time%
Linux:
echo "Current date and time: $(date)"
Task 6: Trigger by SCM (Git)
• Create a project GitJob.
• Connect it to a GitHub repository.
• Configure to pull the latest code.
• In the build step, print the last commit message.
• Verify Jenkins fetches and displays commits.
Solution:
Linux/Windows (Git Bash):
git log -1 --pretty=%B
