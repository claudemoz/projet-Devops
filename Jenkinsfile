pipeline {
  agent any
  stages {
    stage('Clean Workspace') {
      steps {
        deleteDir()
      }
    }
    stage('Checkout SCM') {
      steps {
        git branch: 'main', url: 'https://github.com/claudemoz/projet-Devops.git'
      }
    }
    stage('Build Docker Image') {
      steps {
        script {
          sh 'docker build -t myapp-image .'
        }
      }
    }
  }
}
