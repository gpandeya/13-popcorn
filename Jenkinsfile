pipeline {
  agent any
  stages {
    stage('greeting') {
      steps {
        sh 'echo "hello world!"'
      }
    }
    stage('build docker') {
      steps {
        sh 'docker build -t gpandeya/popcorn:$BUILD_NUMBER .'
      }
    }
    stage('docker push') {
      steps {
        sh '''docker login -u gpandeya -p _________
docker push gpandeya/popcorn:$BUILD_NUMBER'''
      }
    }
  }
}