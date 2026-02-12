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
                    ls -la
                    node --version
                    npm --version
                    export npm_config_cache=$WORKSPACE/.npm-cache
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
