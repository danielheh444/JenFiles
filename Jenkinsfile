pipeline {

   agent any

   environment {
	   login_docker = 'danielheh'		
   }

	
   
   stages {

      stage('Clone Repository') {
         steps {
            git url: 'git@github.com:danielheh444/files.git', branch: 'main', credentialsId: 'GitHub-ssh-key'
            }
        }

      stage('Build Docker Image') {
         steps {
	    script {
               dockerImage = docker.build("${login_docker}/nginx-jen:${env.BUILD_ID}")
            }
         }
     
      }
       
      stage ('Push Registry') {
         steps {
            script {
               docker.withRegistry('https://index.docker.io/v1/', 'cred-for-docker-hub'){
                  dockerImage.push("latest")
               }
            }
         }
      }


   }
}
