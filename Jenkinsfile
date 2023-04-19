pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh '''
#!bin/bash
checkout scm
def customImage = docker.build("${registry}:${env.BUILD_ID}")'''
      }
    }

    stage('deploy') {
      steps {
        sh '''docker.withRegistry(\'\', \'dockerhub_id\') {
        docker.image("${registry}:${env.BUILD_ID}").push(\'latest\')
      }'''
        }
      }

    }
    environment {
      registry = 'armensadoyan/ci-cd'
    }
  }