pipeline{
    agent any
    stages{
        stage('1-repoClone'){
            steps{
                sh 'df -h'
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
        stage('5-welcome message'){
            echo "welcome to pipeline as code"
        }
    }
}