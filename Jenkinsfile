pipeline {
  agent any
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
        sh 'sudo docker build -f curriculum-front/Dockerfile -t mychatgpt/curriculum-front:latest .'
      }
    }

    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'mychatgpt'
        DOCKERHUB_PASSWORD = 'dckr_pat_UCHJSl684kZ0bZ5peCL9kcqTV-U'
      }
      steps {
        sh 'sudo docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('Push') {
      steps {
        sh 'sudo docker push mychatgpt/curriculum-front:latest'
      }
    }

  }
}