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
   }
}
