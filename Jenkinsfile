 pipeline {
    agent any

    stages {
        stage('Checkout') {
              steps {
                  echo 'Downloading project from GitHub'
                  checkout scm
              }
          }


        stage('Setup Python (dind)') {
            steps {
                // if your Jenkins agent is like docker:dind (Alpine) and has no python
                sh '''
                  if ! command -v python3 >/dev/null 2>&1; then
                    echo "Python3 not found, installing..."
                    apk update
                    apk add --no-cache python3 py3-pip
                     ln -sf python3 /usr/bin/python || true
                  fi
                '''
            }
        }

        stage('Run script') {
            steps {
                sh 'python3 script1.py'
            }
        }
             stage('cleaning') {
            steps {
               echo 'cleaning'
            }
        }
    }
}
