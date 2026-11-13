EXPERIMENT 8 - JENKINS CI PIPELINE

Project: simple-calculator-jenkins

Project files:
- pom.xml: Maven configuration and JUnit 5 dependencies
- Jenkinsfile: Jenkins pipeline stages
- src/main/java/com/calculator/Calculator.java: calculator source code
- src/test/java/com/calculator/CalculatorTest.java: JUnit test cases

Run locally from this project folder:
    mvn validate
    mvn clean package

Expected result: BUILD SUCCESS
Maven creates the target folder with the JAR and Surefire test reports.

GitHub:
Create a repository named simple-calculator-jenkins, then run:
    git init
    git add .
    git commit -m "Initial calculator project"
    git branch -M main
    git remote add origin https://github.com/USERNAME/simple-calculator-jenkins.git
    git push -u origin main

Replace USERNAME with your GitHub username.

Jenkins:
Create a Pipeline job. For the webhook version, enable:
    GitHub hook trigger for GITScm polling

Pipeline configuration:
    Definition: Pipeline script from SCM
    SCM: Git
    Repository URL: Your GitHub repository HTTPS URL
    Branch Specifier: */main
    Script Path: Jenkinsfile

This Jenkinsfile uses Windows batch commands (bat), as in the Windows setup.
If Jenkins runs on Linux, change bat to sh.

Webhook/ngrok:
Start Jenkins at http://localhost:8080
Run ngrok:
    ngrok http 8080

In GitHub repository Settings > Webhooks > Add webhook:
    Payload URL: https://YOUR-NGROK-URL/github-webhook/
    Content type: application/json
    Events: Just the push event

Keep the ngrok terminal running while testing. The public ngrok URL can change
when a new tunnel is started, so update the GitHub webhook URL if it changes.
