pipeline {
    agent any
    tools {
        nodejs 'Node 12.16.1'
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Hello World'
                sh 'npm install'
            }
        }
    }
}