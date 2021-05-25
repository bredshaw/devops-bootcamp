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
//        stage('SonarScan') {
//            steps {
//              withSonarQubeEnv('My SonarQube Server') {
//                 sh 'mvn clean package sonar:sonar'
//              }            
//            }
//        }
        stage('createDockerImage') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerRepo', passwordVariable: 'AWS_SECRET_ACCESS_KEY', usernameVariable: 'AWS_ACCESS_KEY_ID')]) {
                    // some block
                    sh '''
                        wget https://download.docker.com/linux/ubuntu/dists/bionic/pool/stable/amd64/docker-ce-cli_18.09.9~3-0~ubuntu-bionic_amd64.deb
                        dpkg -i ./docker-ce-cli_18.09.9~3-0~ubuntu-bionic_amd64.deb
                        apt-get update
                        apt-get install -y awscli
                        docker build -t workshopuser4:latest .
                        docker tag workshopuser4:latest workshopuser4:${BUILD_NUMBER}
                        docker tag workshopuser4:latest 686567993080.dkr.ecr.us-east-1.amazonaws.com/devopsbootcampuser4:latest
                        $(aws ecr get-login --region us-east-1 | sed 's/-e none//g')
                        docker push 686567993080.dkr.ecr.us-east-1.amazonaws.com/devopsbootcampuser4:latest
                    '''
                }
            }
        }
    }
}