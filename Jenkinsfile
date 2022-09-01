pipeline {
  agent any
  environment {
      PATH = "/opt/maven/apache-maven-3.8.6/bin:$PATH"
  }
  stages {
    stage('Build') {
      steps {
        sh "mvn clean install"
      }
    }
    stage('Deploy') {
      steps {   
         deploy adapters: [tomcat8(path: '', url: 'http://3.111.29.216:8090/')], contextPath: null, war: '**/**.war'
      }
    }
  }
}
