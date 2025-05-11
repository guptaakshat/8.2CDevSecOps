pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                script {
                    git branch: 'main', url: 'https://github.com/guptaakshat/8.2CDevSecOps.git', credentialsId: 'GitHub-Access'
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    sh 'npm test || true' // Allows pipeline to continue despite test failures
                }
            }
        }
        stage('Generate Coverage Report') {
            steps {
                script {
                    sh 'npm run coverage || true'
                }
            }
        }
        stage('NPM Audit (Security Scan)') {
            steps {
                script {
                    sh 'npm audit || true' // This will show known CVEs in the output
                }
            }
        }
    }
}
