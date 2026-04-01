stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/RiturajChaudhary/jenkins-proj.git',
                    credentialsId: 'git-cred'
            }
        }
        stage('Check Files') {
        steps {
        sh 'ls -ltr'
        sh 'sudo docker ps'
        }
        }
