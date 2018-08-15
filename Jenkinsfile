pipeline {
    agent {
        kubernetes {
            label 'my-pod-template'
            defaultContainer 'docker'
            yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: some-label-value
spec:
  containers:
  - name: docker
    image: docker:17.12.1-ce-dind
    privileged: true
    
"""
        }
    }
    stages {
        stage('docker') {
            steps {
                container('docker') {
                    sh 'echo build_image'
                    sh 'docker image build -t stuartcbrown/nginxtest .'
                }

            }
        }
    }
}