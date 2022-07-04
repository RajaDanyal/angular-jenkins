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
                bat "npm run test"
            }
        }

        stage("Build") {
            steps {
                bat "npm run build"
            }
        }

        stage("Deploy") {
            steps {
                bat 'node_modules\\.bin\\pm2 delete -s server.js || :'
                bat 'node_modules\\.bin\\pm2 start server.js'

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
