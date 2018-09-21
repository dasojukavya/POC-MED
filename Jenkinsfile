pipeline {
    agent any
   properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '30')), [$class: 'GithubProjectProperty', displayName: '', projectUrlStr: 'https://github.inbcu.com/GMOEngineering/${REPO}/'], [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], pipelineTriggers([])]) 
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello world!"'
            }
        }
    }
}

