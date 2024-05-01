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
          -Dsonar.host.url=http://18.117.156.176:9000 \
          -Dsonar.login=sqp_3a973ad64d1e7f263a964f14733bffe98d72d398"
      }
    }
  }
}
