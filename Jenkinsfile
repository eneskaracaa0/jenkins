pipeline {
   agent any {
        docker { image 'node:22.11.0-alpine3.20' }
    }

    stages {
        stage('Build') {
            steps {

               
                sh 'node --version'
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
