pipeline{
    agent any
    tools {
        maven "mvn"
    }
    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Git checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/HVAksh/Devops-Basic-Project1.git'
            }
        }
        stage('mvn build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('docker image build') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh '''docker build -t maven-app .
                        docker tag  maven-app hvaksh/maven-app:1.1.2
                        docker tag  maven-app hvaksh/maven-app:latest
                        docker push hvaksh/maven-app:latest'''
                    }
                }
                
            }
        }
        stage('Deploy on local') {
            steps {
                sh 'docker stop maven-app'
                sh 'docker rm maven-app'
                sh 'docker run -d -p 9001:8080 --name maven-app -t hvaksh/maven-app:latest'
            }
        }
    }
}
