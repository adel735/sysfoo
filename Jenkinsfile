pipeline {
    agent any
    tools {
        maven 'maven' // Specify your Maven installation name
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'mvn compile'
                // Add your build commands here
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'mvn clean test'                
                // Add your test commands here
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh 'mvn package -DskipTests'
                // Add your deploy commands here
            }
        }
    }
}
