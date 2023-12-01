pipeline {
  agent any
  environment {
    PATH = "/opt/apache-maven-4.0.0-alpha-8/bin:${PATH}"
  }
  stages {
    stage("git clone code") {
      steps{
        git 'https://github.com/nasreentaj55/jenkins-pipelines1.git'
      }
    }
    
    stage("maven build code"){
      steps{
        sh 'mvn clean package'
      }
    }
    stage("maven test code"){
      steps{
        sh 'mvn test'
      }
    }
    stage("tomcat deploy code"){
      steps{
//         sshagent(['maven-deploy']) {
//           sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/$JOB_NAME/target/*.war ec2-user@54.237.24.49:/opt/apache-tomcat-9.0.72/webapps"
//         }
           deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://15.207.54.242:8080/')], contextPath: null, war: '**/*.war'

        }
      }
    }
  }
