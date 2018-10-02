node ("android") {
  checkout scm
  sh 'git log -n 1'
  workspaceUtils.prepareSourceDirectory()
  withinSourcesDirectory {
      sh './gradlew clean'
      sh './gradlew build'
  }
  workspaceUtils.stashSourceDirectory()
}
