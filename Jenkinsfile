pipeline {
  agent any
  environment {
      PATH = "/home/ec2-user/opt/maven/apache-maven-3.8.6/bin/mvn:$PATH"
  }
  stages {
    stage('Build') {
      steps {
        sh '"mvn" -Dmaven.test.failure.ignore clean install'
      }
    }
    stage('Deploy') {
      steps {   
         deploy adapters: [tomcat8(path: '', url: 'http://3.111.29.216:8090/')], contextPath: null, war: '**/**.war'
      }
    }
  }
}
