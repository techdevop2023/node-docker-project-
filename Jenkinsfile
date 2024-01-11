pipeline {
    agent any 
    stages{
        stage("checkout"){
            steps{
             checkout scm 
          }
      }
       stage("Test"){
         steps{
            sh 'sudo apt-get install npm '
            sh 'npm test'
         }  
       }
       stage("Build"){
        steps{
            sh 'npm run build'
        }
       }
       stage("Build Image"){
          steps {
              sh 'docker build -t webapp:1.0 .'
          }
       }
       stage('Docker Push'){
          steps {
            withCredentials([usernamePassword(credentialsId:'docker_hub',passwordVariable: 'DOCKERHUB_PASSWORD',usernameVariable: 'DOCKERHUB_USERNAME')]){
                sh'docker login -u $DOCKERHUB_USERNAME -p $DOCKERHUB_PASSWORD'
                sh 'docker push virendargupta/webapp:1.0'
                sh 'docker agent'
            }
          }
       }
   }
}
