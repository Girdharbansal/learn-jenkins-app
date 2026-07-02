pipeline {
    agent any
    environment{
        NETLIFY_SITE_ID = 'b4eefd0a-ce00-4eb7-b3bd-2bb553fabfe4'
        NETLIFY_AUTH_TOKEN = credentials('Netlify_Token')
    }
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
                    npm ci
                    npm run build
                    '''
            }
        }
        stage('Deploy') {
            agent {
                docker {
                    image 'node:26-alpine3.23'
                    reuseNode true
                }
            }
             steps {
                sh '''
                    npm install netlify-cli
                    node_modules/.bin/netlify --version
                    node_modules/.bin/netlify status
                    node_modules/.bin/netlify deploy --dir=build --prod

                    '''
            }
        }
    }
    post{
        success{
            archiveArtifacts artifacts: 'newDir/**'
                }
        }
    
}
