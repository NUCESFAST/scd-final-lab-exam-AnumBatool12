pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS_ID = 'docker-hub-credentials' // Jenkins credentials ID for Docker Hub
        DOCKER_HUB_REPO_FRONT = 'anumbatool1203/i211186_frontend' 
        DOCKER_HUB_REPO_AUTH = 'anumbatool1203/i211186_auth' 
        DOCKER_HUB_REPO_CLASSROOM = 'anumbatool1203/i211186_classroom' 
        DOCKER_HUB_REPO_EVENT = 'anumbatool1203/i211186_event' 
        DOCKER_HUB_REPO_DB = 'anumbatool1203/i211186_db'
        DOCKER_HUB_REPO_POST = 'anumbatool1203/i211186_post' 
    }

    stages {
        stage('i211186Checkout') {
            steps {
                git 'https://github.com/NUCESFAST/scd-final-lab-exam-AnumBatool12.git'
            }
        }
        stage('i211186Build Auth') {
            steps {
                dir('Auth') {
                    script {
                        docker.build("${DOCKER_HUB_REPO_AUTH}:latest", '.').withRegistry('', "${DOCKER_CREDENTIALS_ID}") {
                            docker.image("${DOCKER_HUB_REPO_AUTH}:latest").push()
                        }
                    }
                }
            }
        }
        stage('i211186Build Classroom') {
            steps {
                dir('Classrooms') {
                    script {
                        docker.build("${DOCKER_HUB_REPO_CLASSROOM}:latest", '.').withRegistry('', "${DOCKER_CREDENTIALS_ID}") {
                            docker.image("${DOCKER_HUB_REPO_CLASSROOM}:latest").push()
                        }
                    }
                }
            }
        }
        stage('i211186Build Event') {
            steps {
                dir('event-bus') {
                    script {
                        docker.build("${DOCKER_HUB_REPO_EVENT}:latest", '.').withRegistry('', "${DOCKER_CREDENTIALS_ID}") {
                            docker.image("${DOCKER_HUB_REPO_EVENT}:latest").push()
                        }
                    }
                }
            }
        }
        stage('i211186Build Frontend') {
            steps {
                dir('client') {
                    script {
                        docker.build("${DOCKER_HUB_REPO_FRONT}:latest", '.').withRegistry('', "${DOCKER_CREDENTIALS_ID}") {
                            docker.image("${DOCKER_HUB_REPO_FRONT}:latest").push()
                        }
                    }
                }
            }
        }
        stage('i211186Build Post') {
            steps {
                dir('client') {
                    script {
                        docker.build("${DOCKER_HUB_REPO_POST}:latest", '.').withRegistry('', "${DOCKER_CREDENTIALS_ID}") {
                            docker.image("${DOCKER_HUB_REPO_POST}:latest").push()
                        }
                    }
                }
            }
        }
        stage('i211186Build DB') {
            steps {
                script {
                    docker.build("${DOCKER_HUB_REPO_DB}:latest", '.').withRegistry('', "${DOCKER_CREDENTIALS_ID}") {
                        docker.image("${DOCKER_HUB_REPO_DB}:latest").push()
                    }
                }
            }
        }
    }
}
