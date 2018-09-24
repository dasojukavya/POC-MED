def serviceName="service"
def slackChannel = "#testing"

try {
properties([
//  [$class: 'BuildConfigProjectProperty', name: '', namespace: '', resourceVersion: '', uid: ''], buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '28')),
  [$class: 'GitlabLogoProperty', repositoryName: ''], [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false],
  [$class: 'ThrottleJobProperty', categories: [], limitOneJobWithMatchingParams: false, maxConcurrentPerNode: 0, maxConcurrentTotal: 0, paramsToUseForLimit: '', throttleEnabled: false, throttleOption: 'project'],
  [$class: 'GithubProjectProperty', displayName: '', projectUrlStr: 'https://github.com/dasojukavya/POC-MED.git/'],
  parameters(
	[stringParam(defaultValue: "VersionNumber", description: 'Enter Version Number', name: 'VersionNumber'),
	stringParam(defaultValue: "Description of Release", description: 'Enter the Jira URL', name: 'Description'),
	booleanParam(defaultValue: false, description: 'Skip UAT', name: 'skipUAT')])
])

node () {
stage("slack Note") {
println "sending slack notification as first step"
slackStart(slackChannel)
}
	
stage("git checkout") {
checkout poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/development']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout'], [$class: 'CleanCheckout'], [$class: 'WipeWorkspace']], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '038e246f-d6d4-457f-9222-0e02c93d835d', url: 'https://github.com/dasojukavya/POC-MED.git']]]
}

stage("git tag-release") {
  sh '''
repo_full_name=$(git config --get remote.origin.url | sed \'s/.*:\\/\\/github.com\\///;s/.git$//\')

generate_post_data()
{
  cat <<EOF
{
  "tag_name": "GMO-MedX-QA-Release-$VersionNumber",
  "target_commitish": "development",
  "name": "GMO-MedX-QA-Release-$VersionNumber",
  "body": "$Description",
  "draft": false,
  "prerelease": false
}
EOF
}

echo "Create release $VersionNumber for repo: $repo_full_name branch: development"
curl --data "$(generate_post_data)" "https://api.github.com/repos/$repo_full_name/releases?access_token=a8ddb984a398e3dfc321502d04f3e83b190eb14d"
'''
println "tag and release completed"
}

stage("running main job") {
	sh 'echo "starting on job shell script with git repo, etc"'
}

stage("slack Complete Notifcation") {
println "completed slack notification as later step"
slackCompleted(slackChannel)
}
	
}} catch (err) {
	currentBuild.result = 'FAILURE'
	throw err
} finally {
	println "oops!!!!"  
}

def slackStart(slackChannel) {
slackSend (channel: slackChannel, 
	   color: "#00BFFF",
	   message: ":sunny: *STARTING* `About to start QA Deployment`\n_Please pause all checkIn untill it is completed_.\nURL: ${env.BUILD_URL}")
}

def slackCompleted(slackChannel) {
slackSend (channel: slackChannel, 
	   color: "#00BFFF",
	   message: ":sunny: *COMPLETED* `QA Deployment is completed`\n_Please continue_.\nURL: ${env.BUILD_URL}")
}
