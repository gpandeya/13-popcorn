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
        sh 'docker build -t popcorn:$BUILD_NUMBER .'
      }
    }
  }
}