def label = "worker-${UUID.randomUUID().toString()}"

podTemplate(label: label, containers: [
  containerTemplate(name: 'kubectl', image: 'lachlanevenson/k8s-kubectl:v1.8.8', command: 'cat', ttyEnabled: true)
],
volumes: [
]) {
  node(label) {
    properties(
      [
        [
          $class  : 'jenkins.model.BuildDiscarderProperty',
          strategy: [
            $class: 'LogRotator',
            numToKeepStr: '50'
          ]
        ],
        pipelineTriggers(
          [
            [
              $class: 'hudson.triggers.TimerTrigger',
              spec  : "*/5 * * * *"
            ]
          ]
        )
      ]
    )

    stage('Run kubectl') {
      container('kubectl') {
        withEnv([
            "ES_URL=elasticsearch.storage:9200"
        ]){
            sh """
               kubectl run -it --rm=true busybox-curl --image=yauritux/busybox-curl --restart=Never -- curl "$ES_URL"
            """
      }
    }
  }
}

/*
podTemplate(label: 'mypod', containers: [
    containerTemplate(name: 'git', image: 'alpine/git', ttyEnabled: true, command: 'cat'),
    containerTemplate(name: 'maven', image: 'maven:3.3.9-jdk-8-alpine', command: 'cat', ttyEnabled: true),
    containerTemplate(name: 'docker', image: 'docker', command: 'cat', ttyEnabled: true)
  ],
  volumes: [
    hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock'),
  ]
  ) {
    node('mypod') {
        stage('Check running containers') {
            container('docker') {
                // example to show you can run docker commands when you mount the socket
                sh 'hostname'
                sh 'hostname -i'
                sh 'docker ps'
            }
        }
        
        stage('Clone repository') {
            container('git') {
                sh 'whoami'
                sh 'hostname -i'
                sh 'git clone -b master https://github.com/lvthillo/hello-world-war.git'
            }
        }

  
        stage('Maven Build') {
            container('maven') {
                dir('hello-world-war/') {
                    sh 'hostname'
                    sh 'hostname -i'
                    sh 'mvn clean install'
                }
            }
        }
    }
}
*/
