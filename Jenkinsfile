pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                sh 'mvn sonar:sonar'
            }
        }
        stage('Security Scan') {
            steps {
                sh 'dependency-check.sh --project "MyProject" --scan .'
            }
        }
        stage('Deploy to Staging') {
            steps {
                sh 'aws deploy ...'  // Add your specific AWS command here
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                sh 'mvn integration-test'
            }
        }
        stage('Deploy to Production') {
            steps {
                sh 'aws deploy ...'  // Add your specific AWS command here
            }
        }
    }
}
