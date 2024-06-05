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
        stage('Checkout') {
            steps {
                git 'https://github.com/NUCESFAST/scd-final-lab-exam-AnumBatool12.git'
            }
        }
        stage('Build Auth') {
            steps {
                dir('Auth') {
                    script {
                        def authImage = docker.build("${DOCKER_HUB_REPO_AUTH}:latest", '.')
                        authImage.push()
                    }
                }
            }
        }
        stage('Build Classroom') {
            steps {
                dir('Classrooms') {
                    script {
                        def classroomImage = docker.build("${DOCKER_HUB_REPO_CLASSROOM}:latest", '.')
                        classroomImage.push()
                    }
                }
            }
        }
        stage('Build Event') {
            steps {
                dir('event-bus') {
                    script {
                        def eventImage = docker.build("${DOCKER_HUB_REPO_EVENT}:latest", '.')
                        eventImage.push()
                    }
                }
            }
        }
        stage('Build Frontend') {
            steps {
                dir('client') {
                    script {
                        def frontendImage = docker.build("${DOCKER_HUB_REPO_FRONT}:latest", '.')
                        frontendImage.push()
                    }
                }
            }
        }
        stage('Build Post') {
            steps {
                dir('client') {
                    script {
                        def postImage = docker.build("${DOCKER_HUB_REPO_POST}:latest", '.')
                        postImage.push()
                    }
                }
            }
        }
        stage('Build DB') {
            steps {
                script {
                    def dbImage = docker.build("${DOCKER_HUB_REPO_DB}:latest", '.')
                    dbImage.push()
                }
            }
        }
    }
}
