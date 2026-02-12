pipeline {
    agent none

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    args '-u node'
                    reuseNode false
                }
            }
            environment {
                NPM_CONFIG_CACHE = "${WORKSPACE}/.npm-cache"
            }
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