pipeline {
agent any
environment {
DOCKERHUB_CREDENTIALS = 'itzsmk'
DOCKERHUB_REPO = 'https://hub.docker.com/repository/docker/itzsmk/devops_project/general'
}
stages {
stage('Checkout') {
steps {
// Checkout code from the repository
checkout scm
}
}
stage('Build Docker Image') {
steps {
script {
// Build the Docker image
docker.build("${DOCKERHUB_REPO}:latest")
}
}
}
stage('Push Docker Image') {
steps {
script {
// Push the Docker image to Docker Hub
docker.withRegistry('https://index.docker.io/v1/', "${DOCKERHUB_CREDENTIALS}") {
docker.image("${DOCKERHUB_REPO}:latest").push('latest')
}
}
}
}
}
post {
always {
// Clean up any resources used by the pipeline
cleanWs()
}
}
}
