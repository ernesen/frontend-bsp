
podTemplate(label: 'build', containers: [
    containerTemplate(name: 'docker', image: 'docker', command: 'cat', ttyEnabled: true)
  ],
  volumes: [
    hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock'),
  ]
  ) {
    node('build') {
      container('docker') {
        sh 'docker version'
      }        
    }  
  }

/*
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
*/
