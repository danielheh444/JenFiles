pipeline {

   agent any

   environment {
	   login_docker = 'danielheh'		
   }

   
   stages {
      stage('Build Docker Image') {
         steps {
	    script {
           def dockerImage = docker.build("${login_docker}/my-nginx:${env.BUILD_ID}")
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
