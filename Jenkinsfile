properties([[$class: 'GithubProjectProperty', displayName: '', projectUrlStr: 'https://github.com/hyunil-shin/jenkins_github_integration.git'], 
            pipelineTriggers([githubPush()])])

node() {    
    checkout scm
    sh 'ls -al'
    //setBuildStatus("Build complete", "SUCCESS");
}

void setBuildStatus(String message, String state) {
  step([
      $class: "GitHubCommitStatusSetter",
      reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/hyunil-shin/jenkins_github_integration"],
      contextSource: [$class: "ManuallyEnteredCommitContextSource", context: "jenkins build status"],
      errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: "UNSTABLE"]],
      statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
  ]);
}
