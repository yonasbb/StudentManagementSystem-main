pipeline {
    agent any

    tools {
        maven 'Maven'   // Ensure Maven is installed and configured in Jenkins
        jdk 'JDK 21'         // Use your installed JDK version
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building project...'
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                bat 'mvn test'
            }
            post {
                always {
                    // Publish JUnit or TestNG results
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the application...'
                bat 'mvn package'
            }
        }
    }
}


