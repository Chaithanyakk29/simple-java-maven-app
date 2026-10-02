pipeline {
    agent any
    tools {
        maven 'MAVEN-HOME'
    }
    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }
    post {
        success {
            emailext(
                to: 'kairamkondachaithanya9@gmail.com',
                subject: "Jenkins SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build #${env.BUILD_NUMBER} completed successfully."
            )
        }

        failure {
            emailext(
                to: 'kairamkondachaithanya9@gmail.com',
                subject: "Jenkins FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build #${env.BUILD_NUMBER} failed. Check Jenkins console output."
            )
        }
    }
}
