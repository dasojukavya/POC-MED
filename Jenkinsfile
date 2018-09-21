properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '30')), [$class: 'GithubProjectProperty', displayName: '', projectUrlStr: 'https://github.inbcu.com/GMOEngineering/${REPO}//'], [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], parameters([[$class: 'ChoiceParameter', choiceType: 'PT_SINGLE_SELECT', description: 'Git repository', filterLength: 1, filterable: false, name: 'REPO', randomName: 'choice-parameter-8227634291611758', script: [$class: 'GroovyScript', fallbackScript: [classpath: [], sandbox: false, script: 'return[\'error\']'], script: [classpath: [], sandbox: false, script: '''return [
\'GMO-Mediator-X:selected\',
\'IMOG-Mediator-X\',
\'Hub-Mediator-X\' 
]
''']]]]), pipelineTriggers([])])


pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello world!"'
            }
        }
    }
}

