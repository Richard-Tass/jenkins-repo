pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages{
    stage('1-git-clone'){
      steps{
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-id', url: 'https://github.com/Richard-Tass/jenkins-repo.git']]])
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
      stage('unittest'){
        steps{
            sh 'mvn test'
        }
    }
    stage('codequality'){
      steps{
        sh 'mvn clean verify sonar:sonar \
  -Dsonar.projectKey=maven-sonarQube-job \
  -Dsonar.host.url=http://ec2-3-238-86-198.compute-1.amazonaws.com:9000 \
  -Dsonar.login=sqp_e0663b68e90a8f63645a06850a98334b384a5b80'
      }
    }
  }
}