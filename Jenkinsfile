pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/AbeerSaxena/Banking-java-project/'
                 echo 'github url checkout'
            }
        }
        stage('codecompile '){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting '){
            steps{
                sh 'mvn test'
            }
        }
        stage('QA'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8091:80 --name c00 myimg /bin/bash'
            }
        }   
    }
}
