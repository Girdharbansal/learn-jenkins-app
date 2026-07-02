pipeline {
    agent any
    environment{
        NETLIFY_SITE_ID = 'b4eefd0a-ce00-4eb7-b3bd-2bb553fabfe4'
        NETLIFY_AUTH_TOKEN = credentials('Netlify_Token')
    }
    stages {
        parallel{
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
                    npm ci
                    npm run build
                    ls -la
                    '''
            }
        }
        stage('Test'){
              agent {
                docker {
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
        }
    }    
}
