pipeline {

   agent any

   environment {
	   login_docker = 'danielheh'		
   }

   
   stages {
      stage('Build Docker Image') {
         steps {
           def dockerImage = docker.build("${login_docker}/my-nginx:${env.BUILD_ID}")
         }
     
      }
       
      stage ('Push Registry') {
         steps {
            dockerImage.push("latest")
         }

      }


   }
}
