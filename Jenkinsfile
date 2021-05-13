pipeline {
    agent any


    stages {
        stage('gitclone') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', credentialsId: '7b67be65-92ac-4c3b-9c28-fbbf15a10647', url: 'https://github.com/subhadipdasgit/apache.git'

            }
        }        
        
        stage ('deploy'){
            steps{
                sh "mv index.html /var/www/html/"
            }
        }   
            
        
    }
}

