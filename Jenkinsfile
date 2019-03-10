node('slave1') {
  stage('checkout') {
    checkout scm
  }
  stage('build') {
    gradleHome = tool 'gradle4'
    sh "${gradleHome}/bin/gradle build"
  }
  stage('unit-test') {
    sh "${gradleHome}/bin/gradle test"
  }
}
