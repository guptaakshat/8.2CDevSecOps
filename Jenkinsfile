pipeline { 
    agent any 
    stages { 
        stage('Checkout') { 
            steps { 
                git branch: 'main', url: 'https://github.com/guptaakshat/8.2CDevSecOps.git', credentialsId: 'GitHub-Access' 
            } 
        } 
        stage('Install Dependencies') { 
            steps { 
                sh 'npm install' 
            } 
        } 
        stage('Run Tests') { 
            steps { 
            } 
        } 
        stage('Generate Coverage Report') { 
            steps { 
            } 
        } 
        stage('NPM Audit (Security Scan)') { 
            steps { 
            } 
        } 
    } 
} 
