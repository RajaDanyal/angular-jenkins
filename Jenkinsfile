#!/usr/bin/env groovy
pipeline {
    agent any

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
