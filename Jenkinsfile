pipeline {
    agent any

    stages {

        stage('Build Maven') {
            steps {
                sh 'java -version'
                sh 'mvn -version'
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t demo-app:1.0 .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop demo-app || true
                docker rm demo-app || true
                docker run -d -p 8080:8080 --name demo-app demo-app:1.0
                '''
            }
        }
    }
}
             
