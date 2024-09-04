/* Requires the Docker Pipeline plugin */
pipeline {
    agent any
    stages {
        stage('Deploy'){
            steps {
                retry(3) {
                    sh './flakey-deploy.sh'
                }

                timeout(time: 1, unit: 'MINUTES'){
                    echo 'failed to deploy flakey!!!'
                }
            }
        }
    }
}