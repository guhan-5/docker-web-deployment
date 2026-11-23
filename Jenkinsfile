pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-web:$BUILD_NUMBER .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                    docker stop devops-web || true
                    docker rm devops-web || true

                    docker run -d \
                    --name devops-web \
                    --restart unless-stopped \
                    -p 81:80 \
                    devops-web:$BUILD_NUMBER
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'curl -f http://localhost:81'
            }
        }
    }
}
