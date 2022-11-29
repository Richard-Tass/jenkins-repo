pipeline{
    agent any
    stages{
        stage('1-repoClone'){
            steps{
                sh'checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '0d2811ba-62ff-4728-bd63-58348c041f3d', url: 'https://github.com/Richard-Tass/team4-git-day1.git']]])'
            }
        }
        stage('2-cpuAnalysis'){
            steps{
                sh 'lscpu'
            }
        }
        stage('3-memoryCheck'){
            steps{
                sh 'free -g'
            }
        }
        stage('4-os-stats'){
            steps{
                sh 'cat /etc/os-release'
            }
        }
        stage('5-greetings'){
            steps{
                echo "welcome to groovy"
            }
        }
    }
}