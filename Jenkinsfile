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
  -Dsonar.projectKey=sonarqube-demo-job \
  -Dsonar.host.url=http://ec2-44-198-171-241.compute-1.amazonaws.com:9000 \
  -Dsonar.login=sqp_4d9170678ed8fbb9e5f135bf6e69aa6cf58f1c73'
      }
    }
  }
}