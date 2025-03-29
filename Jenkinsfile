pipeline {
    agent any

    tools {
        maven 'Maven-3.8.1'  // Make sure this matches your Maven installation in Jenkins
        jdk 'JDK11'          // Make sure JDK11 is configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/your-username/your-repo.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Add deployment steps here if necessary
            }
        }
    }

    triggers {
        pollSCM('H/5 * * * *') // Polls Git for changes every 5 minutes
    }

    post {
        success {
            echo 'Build Successful!'
        }
        failure {
            echo 'Build Failed!'
        }
    }
}


