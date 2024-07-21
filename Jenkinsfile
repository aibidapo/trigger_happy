pipeline {
    agent any

    stages {
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
                    source myenv/bin/activate
                    
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
