pipeline {
    agent {
        
        label 'docker'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                
                    sh 'docker build -t antoniosreda/docker-react -f Dockerfile.dev .'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    env.DOCKER_BUILDKIT = 1
                    sh 'docker run -e CI=true antoniosreda/docker-react npm run test'
                }
            }
        }
    }
}