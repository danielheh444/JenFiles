pipeline {

   agent {label 'comp-1'}

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
               dockerImage = docker.build("${login_docker}/nginx-jen:latest")
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

      stage ('Clean Images') {
         steps {
            sh 'docker rmi -f $(docker images -q)'
         }
      }


   }
}
