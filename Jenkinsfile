pipeline {
    agent any

    stages {
        stage('Echo Content') {
            steps {
               sh echo $(<hook_me_web)
            }
        }
    }
}
