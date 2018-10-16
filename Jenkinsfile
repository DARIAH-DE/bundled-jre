// some methods are imported from
// https://gitlab.gwdg.de/dariah-de/jenkins-shared-library

node {
  def mvnHome

  stage('preparation') {
    mvnHome = tool 'Maven 3.0.4'
    checkout scm
  }

  stage('build') {
    sh "${mvnHome}/bin/mvn clean verify"
  }

  stage('deploy') {
    p2deploy('./updatesite/target/repository', 'bundled-jre')
  }

  stage('Notify') {
    notifyTglabDownstream('lab-base')
  }

}
