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
                sh 'chmod +x ./deploy.sh'
                sh 'chmod +x ./run-smoke-tests.sh'
                sh './deploy.sh staging'
                sh './run-smoke-tests.sh'
            }
        }

        stage('Sanity check') {
            steps {
                input "Does the staging environment look ok?"
            }
        }
        
        stage('Deploy - Production') {
            steps {
                sh './deploy.sh production'
            }
        }
    }
}