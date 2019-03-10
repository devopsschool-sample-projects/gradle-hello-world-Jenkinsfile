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
  stage('int-test') {
    tests = ["one" : { sh "test-data/int-test.sh build/libs/oto-gradle-1.0.jar otoMato 'Hello Otomato!'"}, 
             "two" :{ sh "test-data/int-test.sh build/libs/oto-gradle-1.0.jar anton 'Hello Anton!'" },
             "three" :{ sh "test-data/int-test.sh build/libs/oto-gradle-1.0.jar microfOcuS 'Hello Microfocus!'" }]
    parallel tests
  }
}
