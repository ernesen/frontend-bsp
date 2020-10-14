pipeline {

  agent {
    docker { image 'ernesen/migratecf:3.0' }
  }

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
