pipeline {
  agent{
      label 'slave'
  }
  stages {
    stage('Build') {
      steps {
        sh '"mvn" -Dmaven.test.failure.ignore clean install'
      }
    }
    stage('Deploy') {
      steps {   
         deploy adapters: [tomcat8(credentialsId: 'eeb4e4c4-6a3c-4ca2-bcf8-39d57d004541', path: '', url: '3.109.186.143:8080')], contextPath: null, war: '**/**.war'
      }
    }
  }
}
