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
    stage('Deploy Container') {
      steps {
        script {
          sh '''
          if [ "$(docker ps -aq)" ]; then
            docker rm -f $(docker ps -aq)
          fi
          docker run -d --name monapp --hostname monapp -p 8099:80 myapp-image
          docker exec -it -d monapp "ifconfig"
          '''
        }
      }
    }
  }
}
