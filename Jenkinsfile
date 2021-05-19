pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Hello World'
                nodejs('Node 12.16.1') {
                    sh 'npm install'
                }
            }
        }
    }
}