pipeline {
    agent none

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    args '-u node'
                }
            }
            environment {
                NPM_CONFIG_CACHE = "${WORKSPACE}/.npm-cache"
            }
            steps {
                sh '''
                    set -x
                    whoami
                    node --version
                    npm --version

                    echo "===== npm ci ====="
                    npm ci

                    echo "===== npm build ====="
                    npm run build
                '''
            }
        }
    }
}