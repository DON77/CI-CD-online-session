pipeline {
  agent none
  stages {
    stage('build') {
      steps {
        sh '''checkout scm
def customImage = docker.build("${registry}:${env.BUILD_ID}")'''
      }
    }

  }
  environment {
    registry = 'armensadoyan/ci-cd'
  }
}