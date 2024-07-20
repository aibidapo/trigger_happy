pipeline {
    agent any

    stages {
        stage('Create Directory and Copy File') {
            steps {
                script {
                    sh '''
                    mkdir -p whoami
                    cp hook_me_web whoami/
                    '''
                }
            }
        }
        // stage('Echo Content') {
        //     steps {
        //         script {
        //             def hookMeWebContent = readFile 'hook_me_web'
        //             sh "echo ${hookMeWebContent}"
        //         }
        //     }
        // }
    }
}
