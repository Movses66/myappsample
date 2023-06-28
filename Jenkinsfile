pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build Docker image
                    docker.build("docker:${stage.BUILD_NUMBER}")
                }
            }
        }

        stage('Test') {
            steps {
                // Run tests inside the Docker container
                script {
                    docker.image("docker:${stage.BUILD_NUMBER}")
                          .withRun('-p 8080:8080') {
                        sh 'docker exec -t <container_id> npm test'
                    }
                }
            }
        }

        stage('Push') {
            steps {
                script {
                    // Push Docker image to a container registry
                    docker.withRegistry('https://docker.registry.com', 'docker-credentials') {
                        docker.image("docker:${stage.BUILD_NUMBER}")
                              .push()
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deploy the Docker container to a server
                    sshagent(['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']) {
                        sh 'ssh user@server "docker pull my-docker-image:${env.BUILD_NUMBER} && docker run -d -p 8080:8080 my-docker-image:${env.BUILD_NUMBER}"'
                    }
                }
            }
        }
    }
}
