pipeline {
    agent any
    
    tools {
        maven 'M3_8_6'
    }

    stages {

        stage('Validate') {
            steps {
                dir('servicios/microservicios') {
                    withSonarQubeEnv('sonarqube') {
                        sh "mvn clean install sonar:sonar \
                            -Dsonar.projectKey=22_MyCompany_Microservice \
                            -Dsonar.projectName=22_MyCompany_Microservice \
                            -Dsonar.sources=src/main \
                            -Dsonar.coverage.exclusions=**/*TO.java,**/*DO.java,**/curso/web/**/*,**/curso/persistence/**/*,**/curso/commons/**/*,**/curso/model/**/* \
                            -Dsonar.coverage.jacoco.xmlReportPaths=target/site/jacoco/jacoco.xml"
                    }
                }
            }
        }

        stage('Compile') {
            steps {
                dir('servicios/microservicios') {
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
