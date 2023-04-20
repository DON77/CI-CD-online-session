pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        script {
          checkout scm
          def customImage = docker.build("${registry}:${env.BUILD_ID}")
        }

      }
    }

    stage('deploy') {
      steps {
        script {
          docker.withRegistry('', 'docker-id-ci') {
            docker.image("${registry}:${env.BUILD_ID}").push('latest')
          }
        }

      }
    }

  }
  environment {
    registry = 'armensadoyan/ci-cd'
  }
}