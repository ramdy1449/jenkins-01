pipeline {
  agent any
  tools {
    maven 'Maven'
  }
  stages{
    stage('1-cloning project repo'){
      steps{
        checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/ramdy1449/jenkins_1.git']])
      }
    }
    stage('2-cleanws'){
      steps{
        sh 'mvn clean'
      }
    }
    stage('3-mavenbuild'){
      steps{
        sh 'mvn package'
      }
    }
    stage('codequality'){
        steps{
       sh "mvn clean verify sonar:sonar \
  -Dsonar.projectKey=test \
  -Dsonar.projectName='test' \
  -Dsonar.host.url=http://18.217.122.212:9000 \
  -Dsonar.token=sqp_339f8bf63556c5c6dfe3e3f66d60ee0498785016"
      }
    }
  }
}
