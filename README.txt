set up SonarCloud
1. Create a SonarCloud Account:
Go to sonarcloud.io and sign up/log in (you can use your GitHub/GitLab/Bitbucket account).

2. Create a New Project:
Once logged in, click the "+" icon or "Analyze new project".
Import your organization from GitHub/GitLab/Bitbucket.
Select the repository where you pushed your index.html.
Choose "With Jenkins" for the analysis method.
Follow the instructions to set up the project. SonarCloud will give you a Project Key and a Token. Keep these safe.

Part 3: Set up Jenkins
You'll need a running Jenkins instance. If you don't have one, the easiest way is with Docker:

2. Install Necessary Jenkins Plugins:
Go to Manage Jenkins > Manage Plugins > Available plugins and install:
SonarQube Scanner
Pipeline (usually installed by default)
Git (usually installed by default)
3. Configure SonarQube Scanner Global Tool:
Go to Manage Jenkins > Global Tool Configuration.
Scroll to "SonarQube Scanner".
Click "Add SonarQube Scanner".
Give it a Name (e.g., SonarScanner).
Select "Install automatically" and choose the latest version.
Click Save.
4. Configure SonarCloud in Jenkins:
Go to Manage Jenkins > Configure System.
Scroll down to "SonarQube servers".
Click "Add SonarQube".
Name: SonarCloud (or similar)
Server URL: https://sonarcloud.io
Authentication Token:
Click "Add" > "Jenkins".
Kind: "Secret text"
Secret: Paste your SonarCloud user token (the one you generated on SonarCloud for your account).
ID: sonarcloud-token (or similar, remember this ID)
Description: SonarCloud User Token
Click Add.
Select the newly created token from the dropdown.
Click Save.



Part 4: Create Jenkins Pipeline
Now, let's define the CI/CD pipeline in a Jenkinsfile that Jenkins will use.
1. Create Jenkinsfile in your repository:
Place this file at the root of your Git repository, alongside index.html



