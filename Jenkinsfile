pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/krishnarjunaraon/spring-petclinic.git']])
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('Docker Build Image') {
            steps {
              sudo sh 'docker build -t my-image -f Dockerfile .'
            }
        }
        stage('Login') {
      steps {
        sh 'docker login -u "krishna1116" -p "Krish@116" docker.io'
     withCredentials([usernameColonPassword(credentialsId: 'Dockerhub', variable: 'Dockerhub')]) {
    // some block
}
      }
    }
    }
}
