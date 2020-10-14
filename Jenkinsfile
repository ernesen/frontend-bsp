pipeline {

  agent any

  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/andreipope/HelloWorld'
      }
    }

    stage('Install dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
         sh 'npm test'
      }
    }      
  }
}
