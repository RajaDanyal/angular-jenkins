pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        echo 'Checkout master branch'
        checkout scm
        
          bat 'npm install'
      }
    }
    stage('Build') {
      steps {
        echo 'Building..'
        dir('webapp') {
          bat 'npm run build'
        }
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
        dir('webapp') {
          bat 'ng serve'
        }
      }
    }
  }
  post {
    success {
      slackSend(color: '#00FF00', message: "Build Successful")
    }
    failure {
      slackSend(color: '#FF0000', message: "Build Failed")
    }
  }
}