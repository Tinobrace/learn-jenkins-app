pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    mkdir -p .npm-cache
                    npm config set cache $(pwd)/.npm-cache --global
                    ls -la
                    node --version
                    npm --version
                    npm ci --unsafe-perm
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
