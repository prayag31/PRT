pipeline {
  agent any

  stages {
    stage('Pull Code') {
      steps {
        checkout scm
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t prt-cicd:latest .'
      }
    }

    stage('Run Docker Container') {
      steps {
        sh 'docker run --rm prt-cicd:latest'
      }
    }
  }

  post {
    success {
      echo 'Pipeline completed successfully!'
    }
    failure {
      echo 'Pipeline failed!'
    }
    always {
      sh 'docker image prune -f || true'
    }
  }
}
