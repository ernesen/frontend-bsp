
pipeline {
  environment {
    DOCKER_TAG = getDockerTag()
    registry = "ernesen/frontend-bsp:2.0"
    registryCredential = 'DockerCredentials'
    dockerImage = ''
    BUILD_NUMBER = $BUILD_NUMBER+".0"
  }
  
  agent {
    docker { image 'ernesen/migratecf:3.0' }
  }

  stages {
    stage('Building image') {
      steps{
        sh "'Building image'"
      }
    }

    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
    stage('Send Slack notifications') {
      steps{
        sh "echo Send Slack notifications'"
      }
    }
  }
}

def getDockerTag(){
    def tag  = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag
}

def getContext(environment) {
    return (env.BRANCH_NAME == 'master') ? environment : 'dev'
}

def notify(status){
    emailext (
      to: "ernese@sg.ibm.com",
      subject: "${status}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: """<p>${status}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
        <p>Check console output at <a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a></p>""",
    )
}
