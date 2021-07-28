pipeline {
    agent any
    tools {nodejs "nodejs"}
    stages {
        stage('build') {
            steps {
                echo 'Build'
		sh 'npm install'
            }
        }
        stage('test') {
            steps {
                echo 'Test'
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
                sh '''#!/usr/bin/env bash
                docker login -u ${DOCKER_REGISTRY_USERNAME} -p ${DOCKER_REGISTRY_PASSWORD}
                docker build --tag "${REGISTRY_NAME}/nodejs-demo-mb:${BUILD_NUMBER}" .
                docker push "${REGISTRY_NAME}/nodejs-demo-mb:${BUILD_NUMBER}"
                docker run --rm "${REGISTRY_NAME}/nodejs-demo-mb:${BUILD_NUMBER}"
                '''
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
