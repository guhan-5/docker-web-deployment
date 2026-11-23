pipeline {
    agent any

    stages {
        stage('Check Docker') {
            steps {
                sh 'docker --version'
            }
        }

        stage('Check Container') {
            steps {
                sh 'docker ps'
            }
        }
    }
}
