pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'myapp_image'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/muhammadumarrasheed/cicd-myapp.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(DOCKER_IMAGE, '.')
                }
            }
        }

        stage('Run Application') {
            steps {
                script {
                    docker.image(DOCKER_IMAGE).run('-p 3005:3005')
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}


