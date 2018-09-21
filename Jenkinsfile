pipeline {
    agent any
//   properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '30')), [$class: 'GithubProjectProperty', displayName: '', projectUrlStr: 'https://github.inbcu.com/GMOEngineering/${REPO}/'], [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], pipelineTriggers([])]) 
  parameters {
        string(defaultValue: "TEST", description: 'What environment?', name: 'userFlag')
        choice(choices: ['US-EAST-1', 'US-WEST-2'], description: 'What AWS region?', name: 'region')
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello world!"'
            }
        }
    }
}
