pipeline {
    agent any

    stages {
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
