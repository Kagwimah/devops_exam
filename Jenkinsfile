
// Initialize a LinkedHashMap / object to share between stages
def pipelineContext = [:]

pipeline {
    agent any

    environment {
        DOCKER_IMAGE_TAG = "my-app:build-${env.BUILD_ID}"
    }

    stages {
        stage('Configure') {
            steps {
                echo 'Create parameters file'
            }
        }
        stage('Build') {
            steps {
                echo "Build docker image"
                script {
                    dockerImage = docker.build("${env.DOCKER_IMAGE_TAG}",  '-f ./Dockerfile .')
                    pipelineContext.dockerImage = dockerImage
                }
            }
        }
        stage('Run') {
            steps {
                echo "Run docker image"
                script {
                    pipelineContext.dockerContainer = pipelineContext.dockerImage.run()
                }
            }
        }
        stage('Test') {
            steps {
                echo "Testing the app"
            }
        }
    }
