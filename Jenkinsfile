#!/usr/bin/env groovy
pipeline {
    agent any
  
   // now you are on slave labeled with 'label'
    def workspace = WORKSPACE
    // ${workspace} will now contain an absolute path to job workspace on slave

    workspace = env.WORKSPACE
    // ${workspace} will still contain an absolute path to job workspace on slave

    // When using a GString at least later Jenkins versions could only handle the env.WORKSPACE variant:
    echo "Current workspace is ${env.WORKSPACE}"

    // the current Jenkins instances will support the short syntax, too:
    echo "Current workspace is $WORKSPACE"
  

    stages {
        stage("Checkout SCM") {
            steps {
                checkout scm
            }
        }

        stage("NPM Install") {
            steps {
                sh "npm install"
            }
        }

        stage("Run tests") {
            steps {
                sh "ng test --browsers ChromeHeadless"
            }
        }

        stage("Build") {
            steps {
                sh "npm run build"
            }
        }

        stage("Deploy") {
            steps {
                sh "node server.js"
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
