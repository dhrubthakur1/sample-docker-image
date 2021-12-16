pipeline {
  agent any
  stages {
    stage ('Build docker image') {
      steps {
        sh "docker build -t jenkinstraining.azurecr.io/sample-docker-image-66480:$BUILD_NUMBER ."
      }
    }
    stage ('Push docker image to container registry') {
      environment {
        DOCKER_CONFIG = credentials('jenkins-training-docker-config-json')
      }
      steps {
        sh "export DOCKER_CONFIG=\"\$(dirname \"\$DOCKER_CONFIG\")\"; docker push jenkinstraining.azurecr.io/sample-docker-image-66480:$BUILD_NUMBER"
      }
    }
  }
}
