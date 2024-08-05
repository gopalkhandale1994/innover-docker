# Innover Task

This repository contains the implementation of a simple HTML page deployed using Jenkins pipelines.

## Prerequisites

Ensure you have the following installed on your Linux machine:
- Git
- Docker
- Java (JRE and JDK)
- Jenkins
- Apache2

## Installation Steps

### Install Docker

```bash
sudo apt-get update
sudo apt-get install docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

### Install Git

```bash
sudo apt-get install git
```

### Install Java

```bash
sudo apt install default-jre
sudo apt install default-jdk
```

### Install Jenkins

```bash
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

### Install Apache2

```bash
sudo apt-get install apache2
```

## Project Structure

- `Docker/`
  - `Dockerfile`
  - `Jenkinsfile`
  - `index.html`

## GitHub Repositories
- [Innover Docker Repository](https://github.com/gopalkhandale1994/innover-docker.git)

## Pushing the Project to GitHub

1. Initialize Git in your project directories:

```bash
cd ../Docker
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/gopalkhandale1994/innover-docker.git
git push -u origin main
```

## Jenkins Pipeline Setup


### Pipeline for Docker Deployment

1. Open Jenkins and create a new pipeline job.
2. Configure the pipeline to pull from the `innover-docker` repository.

1. Open Jenkins and create a new Freestyle project and Pipeline Project .
2. Under `Source Code Management`, select `Git` and enter the repository URL: `https://github.com/gopalkhandale1994/innover-docker.git`.
3. Under `Build`, add a `Execute shell` build step with the  command.
4. in Pipeline project add Check the box `GitHub hook trigger for GITScm polling` it will add the Jenkinsfile from remote repo.

### Plugins

Ensure the following plugins are installed in Jenkins:
- Git Plugin
- Pipeline Plugin
- Docker Pipeline Plugin
- GitHub Integration Plugin

To install plugins:
1. Go to `Manage Jenkins` > `Manage Plugins` > `Available`.
2. Search for each plugin and install them.

### Configuring Webhooks

To set up webhooks for automatic builds:

1. **GitHub Repository Settings**:
   - Go to your GitHub repository.
   - Navigate to `Settings` > `Webhooks` > `Add webhook`.
   - Enter the Jenkins URL followed by `/github-webhook/` (e.g., `http://your-jenkins-url/github-webhook/`).
   - Choose `application/json` as the content type.
   - Select the events you want to trigger the webhook (usually `Push` and `Pull Request` events).

2. **Jenkins Job Configuration**:
   - In your Jenkins job, go to `Build Triggers`.
   - Check the box `GitHub hook trigger for GITScm polling`.

## Accessing the Services
- Dockerized Application: [http://34.44.198.225:8000](http://34.44.198.225:8000)

## Conclusion

This project demonstrates a simple CI/CD pipeline setup using Jenkins for both a basic HTML page and a Dockerized application. The HTML page is deployed to an Apache server, while the Dockerized application runs on port 8000.
