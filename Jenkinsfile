pipeline {
    agent any

    stages {
        stage('Install python3-venv') {
            steps {
                sh '''
                sudo apt-get update
                sudo apt-get install -y python3-venv
                '''
            }
        }
        stage('Setup Virtual Environment') {
            steps {
                sh '''
                python3 -m venv myenv
                '''
            }
        }
        stage('Create Directory, Copy File, and Run Python') {
            steps {
                script {
                    sh '''
                    # Create a directory and copy the file
                    mkdir -p whoami
                    cp hook_me_web whoami/
                    
                    # Activate the virtual environment
                    . myenv/bin/activate
                    
                    # Run Python commands
                    python -c "
import os
print('Current directory contents:')
print(os.listdir('whoami'))
"
                    '''
                }
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
