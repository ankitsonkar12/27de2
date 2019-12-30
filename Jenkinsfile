pipeline{
    agent any
    tools{
        maven "m3"
        jdk "jdk8"
    
    }
    triggers{
        pollSCM("* * * * *")
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
        stage('test'){
            steps{
                sh "mvn test"
            }
        }
        stage('Test Report') {
          steps {
              script {
                junit '**/surefire-reports/*.xml'
              }
          }
        }
        stage('package'){
            steps{
                sh "mvn package"
            }
        }
        stage('sonarqube'){
            steps{
                withSonarQubeEnv(credentialsId:"sonar27",installationName:"sonar7.6"){
                    sh "mvn sonar:sonar"
                }
            }
        }
        stage('artifacts')
        {
            steps{
                nexusArtifactUploader artifacts :[[artifactId:'MyWebApp',classifier:'',file:'/var/lib/jenkins/workspace/27dec5/target/ci-pipeline-pragra-0.0.1.jar',type:'jar']],credentialsId:'nexus4',nexusVersion:'nexus3',protocol:'http',nexusUrl:'18.220.86.161:8081',groupId:'org.springframework.boot',version:'1.0-SNAPSHOT',repository:'nexus1'
            }
        }
    }
}
