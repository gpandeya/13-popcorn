pipeline {

 agent any

 environment {
   DOCKER_PASSWORD = credentials ('DOCKER_PASSWORD')
 }

 stages {
 
   stage('greetings'){
     steps {
       sh 'echo "hello work"'
     }
   }

   stage('build docker'){

     steps{

       sh 'docker build -t gpandeya/popcorn:$BUILD_NUMBER .'
     }

   }

 stage('testing') {

     steps {

       sh 'docker run gpandeya/popcorn:$BUILD_NUMBER rails test'

     }

   }
   stage('docker push') {

     steps {

       sh '''docker login -u gpandeya -p $DOCKER_PASSWORD

      docker push gpandeya/popcorn:$BUILD_NUMBER'''

     }

   }
   
   stage('deploy to k8s') {

     steps {

       sh ''' envsubst  < deployment.yaml | kubectl apply -f -
    '''

     }

   }

 }

}