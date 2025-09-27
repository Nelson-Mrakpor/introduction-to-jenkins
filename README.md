# Introduction to Jenkins

This project provides an introduction to **Jenkins**, a powerful and
widely used Continuous Integration and Continuous Delivery (CI/CD) tool
for automating software development workflows. It covers the
foundational concepts of CI/CD, installation and configuration of
Jenkins, navigating the Jenkins user interface, creating and managing
jobs, and automating software builds, tests, and deployments.

## Installing Jenkins

### Step 1: Update Packages

Ensure all packages in your Linux environment are up to date:

``` bash
sudo apt update
```

### Step 2: Install JDK

Jenkins requires Java to run. Install the default JDK with:

``` bash
sudo apt install default-jdk-headless
```

### Step 3: Install Jenkins

Add the Jenkins repository, import the GPG key, update the package list,
and install Jenkins:

``` bash
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt-get install jenkins
```

### Step 4: Verify Installation

Check the Jenkins service status:

``` bash
sudo systemctl status jenkins
```

![Jenkins Status](jenkins-status.png)

## Setting Up Jenkins

Open your web browser and navigate to:

`http://localhost:8080`

![Unlock Jenkins](unlock-jenkins.png)

Retrieve the initial admin password from your terminal:

``` bash
cat /var/lib/jenkins/secrets/initialAdminPassword
```

Paste the password in the web UI and click **Continue**.\
Next, select **Install suggested plugins** to complete setup.

![Suggested Plugins](suggested-plugins.png)

Then, create your first admin user:

![Admin User](admin-user.png)

Log in with your newly created account:

![Admin Sign-In](jenkins-sign-in.png)

## Creating a Freestyle Project

In Jenkins, a **job** is a task that automates parts of the build or
deployment process, such as compiling code, running tests, or packaging
applications.

From the Jenkins dashboard, click **New Item**:

![New Item](new-job.png)

Name the job (e.g., `my-first-job`), select **Freestyle project**, and
click **OK**.

![My First Job](my-first-job.png)

Next, create a GitHub repository (e.g., `jenkins-scm`) with a
`README.md` file:

![Jenkins SCM Repo](jenkins-scm-repo.png)

Back in Jenkins, open your project configuration, select **Git** under
**Source Code Management**, and provide your repository URL and GitHub
Personal Access Token. Choose the branch `*/main` and save.

![Repository URL](repo-url.png)

Return to the Jenkins dashboard, click the job name, and select **Build
Now** to run your first build.\
At this point, Jenkins is successfully connected to your GitHub
repository.

## Configuring Build Triggers

To automate builds when changes are made to the repository, configure a
build trigger.

From your project configuration page, scroll to **Build Triggers** and
enable **Poll SCM**. Enter the following schedule:

    H/1 * * * *

This instructs Jenkins to check for changes every minute.

![Jenkins Trigger](jenkins-trigger.png)

## Conclusion

By completing this project, you have successfully installed and
configured Jenkins, created and connected a freestyle project to GitHub,
and set up automated build triggers. With these foundations, you can now
expand into advanced Jenkins capabilities such as pipelines, integration
with Docker and Kubernetes, and deployment automation. Jenkins is a
versatile tool that can significantly improve the efficiency,
reliability, and scalability of modern software development workflows.
