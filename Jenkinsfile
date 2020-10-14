podTemplate(
  label: 'jenkins-pipeline', 
  inheritFrom: 'default',
  containers: [
  ]
) {
  node ('jenkins-pipeline') {
    stage('Get latest version of code') {
      checkout scm
    }

    stage('Code Formatting checks') {
    }

    stage('Build') {
    }

    stage('Run Unit Tests') {
    }

    stage('Run Code Coverage') {
    }

    stage('Deploy Local') {
    }

    stage('Run Integration Tests') {
    }

    stage('Deploy Production') {
    }
    
    stage('Run Post Deployment Tests') {
    }
  } // end node
} // end podTemplate
