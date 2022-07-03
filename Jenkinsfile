#!/usr/bin/env groovy
pipeline {
    agent any

    stages {
        stage("Checkout SCM") {
            steps {
                Checkout scm
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