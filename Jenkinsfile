pipeline {
    agent any
  tools {
    maven 'MAVEN3'
}
    stages {

        stage('Build Maven') {
            steps {
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
