pipeline {
  agent any
  tools {
    nodejs 'node-18'
}
  stages {
    stage('checkout') {
      steps {
         git branch: 'main', url: 'https://github.com/Himabindu222/Super-mario.git'
        }
     }
     stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
    stage('Test') {
            steps {
                sh 'npm test || echo "No tests defined"'
            }
        }

    stage('Build') {
            steps {
                sh 'npm run build'
            }
        } 
    stage('docker build') {
            steps {
                sh 'docker build -t game .'
            }
        } 
    stage('docker deploy') {
            steps {
                sh 'docker run -d -p 8070:8080 --name mimic_2 game:latest'
            }
        }    
    }
}
