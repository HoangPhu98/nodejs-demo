pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'echo Build'
            }
        }
        stage('test') {
            steps {
                sh 'echo test'
            }
        }
        stage('For the fix branch') {
          when {
            branch 'fix-*'
          }
            steps {
                echo "fix-* branch"
            }
        }
        stage('For the MR') {
          when {
            branch 'MR-*'
          }
            steps {
                echo "This is for MR"
            }
        }
    }
}
