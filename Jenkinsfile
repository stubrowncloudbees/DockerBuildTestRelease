pipeline {
  agent {
    kubernetes {
      label 'my-pod-template'
      defaultContainer 'jnlp'
      yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: some-label-value
spec:
  containers:
  - name: maven
    image: maven:alpine
    command:
    - cat
    tty: true
  - name: busybox
    image: busybox
    command:
    - cat
    tty: true
  - name: docker
    image: docker:17.12.1-ce-dind
    privileged: true
    command:
    - cat
    tty: true    
"""
    }
  }
  stages {
    stage('docker') {
      steps {
        container('docker')
        sh 'echo build_image'
      }
    }
  }
}