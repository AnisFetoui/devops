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
                    sh 'mvn clean package -DskipTests'
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
                subject: "Échec du pipeline Jenkins - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Le pipeline Jenkins pour le projet a échoué lors de l'étape de création du livrable.\n\nVoir les détails ici : ${env.BUILD_URL}"
        }
    }
}