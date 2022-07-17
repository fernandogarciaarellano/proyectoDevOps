pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                dir('/servicios/microservicios') {
                    sh 'docker build -t microservicio .'
                }
                
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'deploying app'
                sh 'docker images'
            }
        }
    }
}
