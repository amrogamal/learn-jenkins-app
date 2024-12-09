pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -al
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -al
                '''    
            }
        }
    }
        stage('test'){
            agent{
                docker{
                    image 'node;18-alpine'
                }
            steps{
                sh '''
                test -f build/index.html
                nmp test
                '''
            }    
            }

    }
}