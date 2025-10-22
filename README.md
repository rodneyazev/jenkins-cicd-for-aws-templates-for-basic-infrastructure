## An example of using Jenkins to build and deploy an AWS Template for Basic Infrastructure

<i>Build AWS Basic Infra pipelines will use the following GitHub repositories:</i>

- <a href="https://github.com/rodneyazev/aws-templates-for-basic-loadbalancer-and-auto-scaling-infrastructures.git">AWS Templates (Basic Infra)</a>
- <a href="https://github.com/rodneyazev/checking--my-dev-docker-env">A simple Java API (checking--my-dev-docker-env)</a>

### Requirements:

- AWS CLI
- Terraform
- Ansible
- 01 Key Pair (EC2)

<i>P.S.: If you are using any APT GNU/Linux distribution, you can install them using my <a href="https://github.com/rodneyazev/just-a-devops-toolkit-wsl-linux">just-a-devops-toolkit-wsl-linux</a></i>

<p align="center">
  <img src="img/logo-cicd.png" alt="logo" style="width: 60%"/>
</p>

<i>Don't forget to prepare your Jenkins environment by running the following pipelines:</i>

- Install Basic Applications
- Install DevTools

# Jenkins

### Install Jenkins container:

```
docker compose -f jenkins.yml up -d
```

### Get Jenkins password:

```
docker exec -it jenkins /bin/bash -c "cat /var/jenkins_home/secrets/initialAdminPassword"
```

### Jenkins plugins installation (if nedeed):

- Docker API Plugin
- Docker Commons Plugin
- Docker plugin
- AWS Credentials Plugin
- AWS Web Services SDK
- Amazon EC2 Plugin
- GitHub Plugin

### You will need to copy SSH Keys to Jenkins container:

E.g.:

```
# Create folder
docker exec jenkins mkdir -p /root/.aws

# Copy SSH Keys

docker cp ~/.aws/my-ssh-key-votc.pem jenkins:/root/.aws/
docker cp ~/.aws/my-ssh-key-votc.pem.pub jenkins:/root/.aws/
```

## Jenkins Pipelines

#### Add New Task
<img src="img/jenkins-new-task.png" />

#### Create Pipeline
<img src="img/jenkins-pipeline.png" />

#### Choose one of them, copy its content and save it
<img src="img/jenkins-pipelines.png" />

<br>

<img src="img/jenkins-pipeline-form.png" />

## Changes that can be made

#### Region and S3 name
<img src="img/jenkins-s3-region-and-bucket.png" />

#### GitHub Repository
<img src="img/jenkins-git-repository.png" />

#### SSH Key
<img src="img/jenkins-ssh-key.png" />

## Result:
<img src="img/2 - jenkins.png" />

<br>

<img src="img/3 - jenkins.png" />

<br>

<img src="img/4 - jenkins.png" />


That is it.