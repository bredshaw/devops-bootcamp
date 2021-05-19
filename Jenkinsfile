pipeline {
    agent any
    tools {
        nodejs 'Node 12.16.1'
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Build node.js module'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'run defined test cases'
                sh 'npm test'
            }
        }
    }
}