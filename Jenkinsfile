pipeline{
    agent any
    tools{
        maven "m3"
        jdk "jdk8"
    
    }
    triggers{
        pollScm("* * * * *")
    }
    stages{
        stage('checkout')
        {
            steps{
                checkout scm
            }
        }
        stage('compile')
        {
            steps{
                sh "mvn clean compile"
            }
        }
    }
}
