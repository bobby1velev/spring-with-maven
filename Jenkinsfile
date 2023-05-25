pipeline {
    agent {
        label 'my-second-agent'
    }

    tools {
        nodejs 'nodejs'
        maven 'maven'
        dockerTool 'docker'
    }

    triggers {
        githubPush()
    }

    environment {
        DOCKERHUB_CREDENTIALS = credentials('d04b1552-91a1-463d-8f92-1fca9db9a0f3')
        IMAGE_NAME = 'ultrax1on/mynodejsapp'
    }

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/bobby1velev/spring-with-maven.git'

            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Docker-build') {
            steps {
                sh 'docker build -t ${IMAGE_NAME} -f Dockerfile .'
                sh 'docker tag ${IMAGE_NAME} ${IMAGE_NAME}:${BUILD_NUMBER}'
            }
        }
        stage('Docker-push') {
            steps {
                sh 'docker login -u ${DOCKERHUB_CREDENTIALS_USR} -p ${DOCKERHUB_CREDENTIALS_PSW}' 
                sh 'docker push ${IMAGE_NAME}:${BUILD_NUMBER}'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker container rm -f maven-app || true'
                sh 'docker run -d -p 5000:8080 --name=maven-app ${IMAGE_NAME}'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}