pipeline{
    agent any
    tools{
        maven "m3"
        java "jdk8"

    }
    stages{
        stage('checkout'){
            steps{
                checkout scm
            }
        }
    }
}