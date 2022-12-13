pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages{
    stage('1-git-clone'){
      steps{
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'e887658f-a27b-4cdd-908d-41cf6eeebe37', url: 'https://github.com/Richard-Tass/jenkins-repo.git']]])
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
  -Dsonar.projectKey=etech-team4 \
  -Dsonar.host.url=http://ec2-3-235-6-186.compute-1.amazonaws.com:9000 \
  -Dsonar.login=1'
      }
    }
  }
}