node ("android") {
  checkout scm
  sh 'git log -n 1'
  prepareSourceDirectory()
  withinSourcesDirectory {
      sh './gradlew clean'
      sh './gradlew build'
  }
  stashSourceDirectory()
}

void prepareSourceDirectory() {
    echo '----------> Preparing the source directory...'

    sh 'rm -rf source'
    sh 'mkdir .source'
    sh '[ "*" = "$(echo *)" ] || mv * .source'
    sh 'mv .source source'
    sh '[ ".[!.]*" = "$(echo .[!.]*)" ] || mv .[!.]* source'

    echo '----------> Finished preparing the source directory.'
}

void stashSourceDirectory() {
    echo '----------> Stashing the source directory...'

    stash includes: 'source/**/*', name: 'build', useDefaultExcludes: false

    echo '----------> Finished stashing the source directory.'
}

def withinSourcesDirectory(Closure closure) {
    dir('source') {
        closure.call()
    }
}
