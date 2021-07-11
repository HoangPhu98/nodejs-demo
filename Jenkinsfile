pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                echo Build
            }
        }
        stage('test') {
            steps {
                echo Test
            }
        }
        stage('For feature-* branch') {
            when {
                branch 'feature-*'
            }
            steps {
                echo "Feature branch"
            }
        }
        stage('For fix-* branch') {
            when {
                branch 'fix-*'
            }
            steps {
                echo "Fix branch"
            }
        }
        stage('For MR-* branch') {
            when {
                branch 'MR-*'
            }
            steps {
                echo "MR branch"
            }
        }
        stage('Deploy Dev') {
            when {
                branch 'dev'
            }
            steps {
                echo "dev branch"
            }
        }
        stage('Deploy Staging') {
            when {
                branch 'staging'
            }
            steps {
                echo "staging branch"
            }
        }
        stage('Deploy Staging') {
            when {
                branch 'staging'
            }
            steps {
                echo "staging branch"
            }
        }
        stage('Deploy Prod') {
            when { tag "release-*" }
            steps {
                echo 'Deploying only because this commit is tagged...'
            }
        }
    }
}
