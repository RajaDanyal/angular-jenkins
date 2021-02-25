pipeline {
  agent any
  stages {
    stage('NPM Install') {
      steps {
        echo 'Checkout master branch'
        checkout scm
        bat 'npm install'
      }
    }
    stage('Build') {
      steps {
        echo 'Building..'
        bat 'npm run build'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
        bat 'npm start'
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