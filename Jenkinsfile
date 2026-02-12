pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            args '-u node'
        }
    }

    environment {
        NPM_CONFIG_CACHE = "${WORKSPACE}/.npm-cache"
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                    whoami
                    node --version
                    npm --version
                    npm ci
                    npm run build
                '''
            }
        }
    }
}