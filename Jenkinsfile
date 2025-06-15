pipeline {
    agent any

    tools {
        maven 'Maven'   // Ensure Maven is installed and configured in Jenkins
        jdk 'Java 21'         // Use your installed JDK version
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building project...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh 'mvn test'
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
                sh 'mvn package'
            }
        }
    }
}


