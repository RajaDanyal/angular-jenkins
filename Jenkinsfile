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
bat '''#!/bin/bash
            if [ -e /root/test/*.php ];then
            echo "Found file"
            else
            echo "Did not find file"
            fi
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
