pipeline {
    agent any

    tools {
        jdk 'java-11'
        maven 'maven'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ManojKRISHNAPPA/test-1.git'
            }
        }

        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

          stage('Build and Tag Docker File') {
            steps {
                sh 'docker build -t vig706/test:1 .'
            }
          }

          stage('Containerisation') {
            steps {
                sh '''
                docker stop c1
                docker rm c1
                docker run -it -d --name c1 -p 8081:8080 vig706/test:1
                '''
            }
        }
        }
    }

