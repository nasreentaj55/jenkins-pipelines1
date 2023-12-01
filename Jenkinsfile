pipeline {
agent any
environment {
PATH = "/opt/apache-maven-4.0.0-alpha-8/bin:${PATH}"
}
stages {
stage('Build the Package') {
steps {
// Building the packages using Maven
sh 'mvn clean package'
}
}

stage('Test the Package') {
steps {
// Testing the packages using Maven Test
sh 'mvn test'
}
}
stage('Deploy the Package') {
steps {
// Deploying the package using TomCat Servers
deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://15.207.54.242:8080/')], contextPath: null, war: '**/*.war'
}
}
}
