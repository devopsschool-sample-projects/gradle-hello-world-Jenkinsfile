node('slave1') {
  stage('checkout') {
    checkout scm
  }
  stage('build') {
    gradleHome = tool 'gradle4'
    sh "${gradleHome}/bin/gradle clean build -x test"
  }
  stage('unit-test') {
    sh "${gradleHome}/bin/gradle test"
    junit "build/test-results/junit-platform/*.xml"
  }
}
