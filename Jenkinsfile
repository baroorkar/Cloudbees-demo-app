pipeline {
    agent {
        kubernetes {
            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: shell
    image: alpine:latest
    command:
    - cat
    tty: true
'''
        }
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub'
            }
        }

        stage('Build') {
            steps {
                container('shell') {
                'sh 'echo Building application inside Kubernetes agent'
                }
            }
        }

        stage('Test') {
            steps {
                container('shell') {
                    sh 'echo Running tests inside Kubernetes agent'
                }
            }
        }

        stage('Deploy') {
            steps {
                container('shell') {
                    sh 'echo Deploying application from Kubernetes agent'
                }
            }
        }
    }
}
