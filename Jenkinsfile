pipeline {
    agent {
        docker {
            image 'node:20-alpine'
            args "-u 110:115" // still using your non-root user
        }
    }
    environment {
        NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"
    }
    stages {
        stage('Install Dependencies') {
            steps {
                sh 'mkdir -p ${NPM_CONFIG_CACHE}'
                sh 'npm ci --cache ${NPM_CONFIG_CACHE}'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        // Add more stages as needed
    }
    post {
        always {
            echo 'Cleaning up...'
            // optional: clean cache if you want
            // sh 'rm -rf ${NPM_CONFIG_CACHE}'
        }
    }
}

