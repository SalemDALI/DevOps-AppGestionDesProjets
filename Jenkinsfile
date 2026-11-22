
pipeline {
    agent any

    tools {
        jdk 'JDK21'
        maven 'M3'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                dir('backend/backend') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage('Test') {
            steps {
                dir('backend/backend') {
                    sh 'mvn test'
                }
            }
        }

        stage('Package') {
            steps {
                dir('backend/backend') {
                    sh 'mvn package -DskipTests'
                }
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts(
                    artifacts: 'backend/backend/target/*.jar',
                    fingerprint: true
                )
            }
        }
    }

    post {
        success {
            echo 'CI Pipeline completed successfully!'
        }

        failure {
            echo 'CI Pipeline failed. Check Console Output.'
        }
    }
}

