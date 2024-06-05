pipeline{
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

    stages{
        stage('i211186_Checkout'){
            steps {
                git 'https://github.com/NUCESFAST/scd-final-lab-exam-AnumBatool12.git'
            }
        }
        stage('i211186_Build_Auth'){ // creating images separetly here
            steps {
                dir('Auth'){
                    script {
                        docker.build("${DOCKER_HUB_REPO_AUTH}:latest", '.')
                    }
                }
            }
        }
        stage('i211186_Build_Classroom'){ // creating images separetly here
            steps {
                dir('Classrooms'){
                    script {
                        docker.build("${DOCKER_HUB_REPO_CLASSROOM}:latest", '.')
                    }
                }
            }
        }
        stage('i211186_Build_Event'){ // creating images separetly here
            steps {
                dir('event-bus'){
                    script {
                        docker.build("${DOCKER_HUB_REPO_EVENT}:latest", '.')
                    }
                }
            }
        }
        stage('i211186_Build_Frontend'){ // creating images separetly here
            steps {
                dir('client'){
                    script {
                        docker.build("${DOCKER_HUB_REPO_FRONT}:latest", '.')
                    }
                }
            }
        }
        stage('i211186_Build_POST'){ // creating images separetly here
            steps {
                dir('client'){
                    script {
                        docker.build("${DOCKER_HUB_REPO_POST}:latest", '.')
                    }
                }
            }
        }
        stage('i211186_Build_DB'){ // creating images separetly here
            steps {
                script {
                    docker.build("${DOCKER_HUB_REPO_DB}:latest", '.')
                }
            }
        }
        stage('Push Images to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('', DOCKER_CREDENTIALS_ID) {
                        docker.image("${DOCKER_HUB_REPO}:latest").push()
                        docker.image("${DOCKER_HUB_REPO}:latest").push()
                        docker.image("${DOCKER_HUB_REPO}:latest").push()
                        docker.image("${DOCKER_HUB_REPO}:latest").push()
                    }
                }
            }
    }
}