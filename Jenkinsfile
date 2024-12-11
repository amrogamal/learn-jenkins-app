pipeline {
    agent any

    stages {
        /*
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
        */

        stage('Save Docker Image') {
            steps {
                sh '''
                # Save the Docker image locally
                docker save -o playwright-deps.tar playwright-image:latest
                '''
            }
        }
        stage('Copy Docker Image to Workspace') {
            steps {
                sh '''
                # Move the image file to the Jenkins workspace
                mv my-docker-image.tar $WORKSPACE/
                '''
            }
        }
        stage('Load Docker Image') {
            steps {
                sh '''
                # Load the Docker image in Jenkins
                docker load -i $WORKSPACE/playwright-deps.tar
                '''
            }
        }
        /*
    
        stage('test'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }        
            steps{
                sh '''
                test -f build/index.html
                npm test
                '''
            }    
            

        }

        stage('E2E'){
            agent{
                docker{
                    image 'mcr.microsoft.com/playwright:v1.49.1-noble'
                    reuseNode true
                }
            }        
            steps{
                sh '''
                   npm install serve
                   node_modules/.bin/serve -s build &
                   sleep 10
                   npx playwright install --with-deps
                   npx playwright test

                
                '''
            }    
            

        }

     
    }
    post{
        success{
            archiveArtifacts artifacts: 'build/**'
        }
        always{
            junit 'jest-results/junit.xml'

        }
        */ 
    }
}
   
