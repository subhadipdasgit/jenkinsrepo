def remote = [:]
remote.name = 'test'
remote.host = '18.209.87.84'
remote.port = 22
remote.allowAnyHosts = true


pipeline {
    agent any


    stages {
        stage('gitclone') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', credentialsId: '7b67be65-92ac-4c3b-9c28-fbbf15a10647', url: 'https://github.com/subhadipdasgit/apache.git'
            }
        }        
        
       stage('Deployment'){
         steps {
            script {
            // move the new changed
            sh '''
             echo "echo hello world" >> test.sh
             cat test.sh
            '''
            sh 'ls'
            withCredentials([usernamePassword(credentialsId: 'bubunid', passwordVariable: 'pass', usernameVariable: 'user')]) {
            remote.user = user
            remote.password = pass
            sshPut remote: remote, from: "index.html", into: "/var/www/html"
            sshPut remote: remote, from: "test.sh", into: "/tmp"
            sshCommand remote: remote, command: "ls /var/www/html && chmod +x /tmp/test.sh"
            sshScript remote: remote, script: 'test.sh'
            }
           }
         }
      }
   }
}
            
        
    


