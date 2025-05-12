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
                    bat 'npm install'
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    bat 'npm test || exit /b 0'
                }
            }
            post {
                always {
                    emailext subject: "Jenkins Build: ${currentBuild.fullDisplayName} - Test Stage",
                             body: """Build ${currentBuild.fullDisplayName} - Test Stage has finished.
                             Check the details at: ${env.BUILD_URL}""",
                             to: 'akshat2001gupta@gmail.com'
                }
            }
        }
        stage('Generate Coverage Report') {
            steps {
                script {
                    bat 'npm run coverage || exit /b 0'
                }
            }
        }
        stage('NPM Audit (Security Scan)') {
            steps {
                script {
                    bat 'npm audit || exit /b 0'
                }
            }
            post {
                always {
                    emailext subject: "Jenkins Build: ${currentBuild.fullDisplayName} - Security Scan",
                             body: """Build ${currentBuild.fullDisplayName} - Security Scan has finished.
                             Check the details at: ${env.BUILD_URL}""",
                             to: 'akshat2001gupta@gmail.com'
                }
            }
        }
    }
}

