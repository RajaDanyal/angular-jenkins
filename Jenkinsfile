#!/usr/bin/env groovy
pipeline {
    agent any
  

    stages {
        stage("Checkout SCM") {
            steps {
              
                echo "Current workspace is ${env.JENKINS_HOME}"

              
                checkout scm
            }
        }

        stage("NPM Install") {
            steps {
                bat "npm install"
            }
        }

        stage("Run tests") {
            steps {
                bat "ng test --browsers ChromeHeadless"
            }
        }

        stage("Build") {
            steps {
                bat "npm run build"
            }
        }

        stage("Deploy") {
            steps {
                bat "node server.js"
            }
        }
    }

    post {
        success {
            echo "SUCCESSFUL"
        }

        failure {
           echo "FAILED"
        }
    }
}
