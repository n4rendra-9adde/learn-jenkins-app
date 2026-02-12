pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            reuseNode false
            args '-u root'  // Run as root to avoid permission issues
        }
    }
    
    stages {
        stage('Debug') {
            steps {
                sh '''
                    echo "=== SYSTEM INFO ==="
                    whoami
                    id
                    df -h
                    free -m
                    echo "=== NODE INFO ==="
                    node --version
                    npm --version
                    echo "=== DISK SPACE ==="
                    du -sh / 2>/dev/null | head -1
                '''
            }
        }
        
        stage('Build') {
            steps {
                sh 'npm ci --verbose'  // Verbose to see where it stops
            }
        }
    }
}