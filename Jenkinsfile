pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                script {
                    git url: 'https://github.com/AnisFetoui/devops.git', branch: 'principal'
                }
            }
        }

        stage('Build Project') {
            steps {
                script {
                    dir('.spring-boot-spring-security-jwt-authentication-master') {
                                            sh 'mvn clean package -DskipTests'
                                        }
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
        failure {
            mail to: 'anisfetoui2000@gmail.com',
                subject: "Échec du pipeline Jenkins - ${env.JOB_NAME} numero : #${env.BUILD_NUMBER}",
                body: "Le pipeline Jenkins pour le Job ${env.JOB_NAME} a échoué lors de l'étape de création du livrable.\n\nVoir les détails ici : ${env.BUILD_URL}"
        }
    }
}