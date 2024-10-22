pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'ls'
                sh 'npm install'
                sh 'echo N | ng analytics off'
                sh 'ng build'
                sh 'ls'
                sh 'cd dist && ls'
                sh 'cd dist/angular-tour-of-heroes/browser && ls'
            }
        }
        stage('S3 Upload') {
            steps {
                AWS(region: 'us-east-2', credentials: 'e5bd1d1e-8423-45ee-9631-006e2ad8c965') {
                    sh 'ls -la'
                    sh 'aws s3 cp dist/angular-tour-of-heroes/browser/. s3://angular-3/ --recursive'
                }
            }
        }
    }
}
