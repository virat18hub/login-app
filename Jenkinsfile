pipeline {
  agent {

    label "slave"
  }
  stages {
    stage("Code Checkout from scm") {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github_key', url: 'https://github.com/panda8899repo/login-app.git']]])
      }
    }
    stage("code quality test by sonarqube") {
      steps{
        echo "Testing The code quality"
        sh "mvn clean install sonar:sonar"
      }
    }
    stage("publish artifact to nexus repo") {
      steps {
        echo "adding artifacts through maven"
        sh "mvn deploy"
      }
    }
  }
}
