pipeline {
    agent any
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '30')), [$class: 'GithubProjectProperty', displayName: '', projectUrlStr: 'https://github.inbcu.com/GMOEngineering/${REPO}/'], [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], parameters([[$class: 'ChoiceParameter', choiceType: 'PT_SINGLE_SELECT', description: 'Git repository', filterLength: 1, filterable: false, name: 'REPO', randomName: 'choice-parameter-8229215733623462', script: [$class: 'GroovyScript', fallbackScript: [classpath: [], sandbox: false, script: '''return[\'error\']

'''], script: [classpath: [], sandbox: false, script: '''return[\'GMO-Mediator-X:selected\']
return[\'IMOG-Mediator-X\']
''']]], choice(choices: ['master development GMO-MedX-QA-Release-3.5 GMO-MedX-Release-17.16 GMO-MedX-Release-18.1 GMO-MedX-QA-Release-3.7.2 GMO-MedX-Release-18.2 GMO-MedX-Release-18.4'], description: 'branch that will be deployed', name: 'BRANCH')]), pipelineTriggers([])])
    
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello world!"'
            }
        }
    }
}

