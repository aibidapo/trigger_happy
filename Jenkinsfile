pipeline {
    agent any

    stages {
        stage('Install python3-venv') {
            steps {
                sh '''
                sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 7EA0A9C3F273FCD8
                sudo apt-get update
                sudo apt-get install -y python3-venv
                '''
            }
        }
        stage('Setup Virtual Environment') {
            steps {
                sh '''
                python3 -m venv medsafe
                '''
            }
        }
        stage('Create Directory, Copy File, and Run Python') {
            steps {
                sh '''
                mkdir -p whoami
                cp hook_me_web whoami/
                . medsafe/bin/activate
                python -c "
import os
print('Current directory contents:')
print(os.listdir('whoami'))
"
                '''
            }
        }
        stage('Echo Content') {
            steps {
                script {
                    def hookMeWebContent = readFile 'hook_me_web'
                    sh "echo ${hookMeWebContent}"
                }
            }
        }
    }
}
