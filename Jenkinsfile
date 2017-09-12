pipeline {
  agent any
  
  environment{
    DOCKER_PASSWORD = credentials('DOCKER_PASSWORD')
  
  }
  stages {
    stage('greeting') {
      steps {
        sh 'echo "hello world!"'
      }
    }
    stage('testing') {
      steps {
        sh ''' rails test
      }
    }
    stage('build docker') {
      steps {
        sh 'docker build -t gpandeya/popcorn:$BUILD_NUMBER .'
      }
    }
    stage('docker push') {
      steps {
        sh '''docker login -u gpandeya -p $DOCKER_PASSWORD
docker push gpandeya/popcorn:$BUILD_NUMBER'''
      }
    }
  }
}