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

        // stage("Run tests") {
        //     steps {
        //         bat "npm run test"
        //     }
        // }

        // stage("Build") {
        //     steps {
        //         bat "npm run build"
        //     }
        // }

        stage("Deploy") {
            steps {
bat '''
call  IF "true"=="true" (
 SET TEST=`pm2 describe server`
 echo $TEST
)
'''
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
