pipeline{
    agent any
    tools{
        maven "m3"
        jdk "jdk8"
    }
    stages{
        stage('checkout')
        {
            steps{
                checkout scm
            }
        }
    }
}