pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/RiturajChaudhary/jenkins-proj.git',
                    credentialsId: 'git-cred'
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'docker-cred',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh '''
                    echo "$DOCKER_PASS" | sudo docker login -u "$DOCKER_USER" --password-stdin
                    '''
                }
            }
        }

        stage('Build Image') {
            steps {
                sh 'sudo docker build -t myapp:latest .'
            }
        }

        stage('Tag Image') {
            steps {
                sh 'sudo docker tag myapp:latest rituraj4164/myapp:v1'
            }
        }

        stage('Push Image') {
            steps {
                sh 'sudo docker push rituraj4164/myapp:v1'
            }
        }
    }
}
