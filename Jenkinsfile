pipeline {
    agent any

    stages {

        stage('Create Directory, Copy File, and Run Python') {
            steps {
                sh '''
                mkdir -p whoami
                cp hook_me_web whoami/
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
