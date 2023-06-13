pipeline {
  agent {
    docker {
      label 'docker-dind'
      image 'jenkins/jnlp-slave' // Or use the appropriate Jenkins agent image with dind support
      args '-v /var/run/docker.sock:/var/run/docker.sock' // Mount the Docker socket from the host
    }
  }
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/theuzumaki1111/curriculum-app', branch: 'main')
      }
    }

    stage('Log') {
      steps {
        sh 'ls -la'
      }
    }

    stage('Build') {
      steps {
        sh 'docker build -f curriculum-front/Dockerfile -t mychatgpt/curriculum-front:latest .'
      }
    }

    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'mychatgpt'
        DOCKERHUB_PASSWORD = credentials('DOCKERHUB_PASSWORD') // Add the Dockerhub password as a Jenkins credential
      }
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('Push') {
      steps {
        sh 'docker push mychatgpt/curriculum-front:latest'
      }
    }
  }
}
