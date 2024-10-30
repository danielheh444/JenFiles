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
               dockerImage = docker.build("${login_docker}/my-nginx:${env.BUILD_ID}")
            }
         }
     
      }
       
      stage ('Push Registry') {
         steps {
            script {
            dockerImage.push("latest")
            }
         }
      }


   }
}
