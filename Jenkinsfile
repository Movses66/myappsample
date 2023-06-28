pipeline {
  agent none

  stages {
    stage('Build') {
      agent {
        docker {
          label 'my-docker-agent'
          image 'your-docker-image:tag' // Specify the Docker image for your job
          args '-v /path/on/host:/path/on/container' // Mount a volume if needed
          reuseNode true // Reuse the agent node for subsequent stages
        }
      }
      steps {
        // Your build steps here
        sh 'echo "Building inside Docker container"'
        sh 'make build' // Example build command
      }
    }
    
    stage('Test') {
      agent {
        docker {
          label 'my-docker-agent'
          image 'your-docker-image:tag'
          args '-v /path/on/host:/path/on/container'
          reuseNode true
        }
      }
      steps {
        // Your test steps here
        sh 'echo "Testing inside Docker container"'
        sh 'make test' // Example test command
      }
    }
    
    // Add more stages as needed
    
    stage('Deploy') {
      agent {
        docker {
          label 'my-docker-agent'
          image 'your-docker-image:tag'
          args '-v /path/on/host:/path/on/container'
          reuseNode true
        }
      }
      steps {
        // Your deployment steps here
        sh 'echo "Deploying inside Docker container"'
        sh 'make deploy' // Example deployment command
      }
    }
  }
}
