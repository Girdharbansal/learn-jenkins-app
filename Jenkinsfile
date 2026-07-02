pipeline {
    agent any
    environment{
        NETLIFY_SITE_ID = 'b4eefd0a-ce00-4eb7-b3bd-2bb553fabfe4'
        NETLIFY_AUTH_TOKEN = credentials('Netlify_Token')
    }
    stages {
       stage('Build') {
            steps {
                echo 'Hello World'
            }
        }
    }    
}
