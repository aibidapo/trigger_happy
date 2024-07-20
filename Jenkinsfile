pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
               git branch: 'main', url: 'https://github.com/aibidapo/trigger_happy.git'
            }
        }
    }
}
