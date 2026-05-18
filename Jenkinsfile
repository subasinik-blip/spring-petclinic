pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/subasinik-blip/spring-petclinic.git'
            }
        }

        stage('Build Application') {
            steps {
                sh './mvnw clean install'
            }
        }

        stage('Test Application') {
            steps {
                sh './mvnw test'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t petclinic .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 8082:8080 petclinic'
            }
        }
    }
}
