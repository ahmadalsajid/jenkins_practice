/* Requires the Docker Pipeline plugin */
pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
            steps {
                echo 'building'
            }
        }
        stage('Test') {
            steps {
                echo 'testing'
            }
        }
        stage('Deploy - Staging') {
            steps {
                bash './deploy staging'
                bash './run-smoke-tests'
            }
        }
        stage('Deploy - Production') {
            steps {
                bash './deploy production'
            }
        }
    }
}