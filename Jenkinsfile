pipeline {

  agent any

  stages {
    stage('Cloning Git') {
      steps {
        sh "echo 'https://github.com/andreipope/HelloWorld'"
      }
    }

    stage('Install dependencies') {
      steps {
        sh "echo 'npm install'"
      }
    }

    stage('Test') {
      steps {
         sh "echo 'npm test'"
      }
    }      
  }
}
