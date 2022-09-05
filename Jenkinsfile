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
    stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarqubeScanner 5.8.0';   ---> this will require in case of installing sonarqube scanner from ssh 
        steps {
          withSonarQubeEnv('sonarqube-8.9.2') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
            sh "mvn sonar:sonar"
          }
        }
      }
    stage('Deploy') {
      steps {   
         deploy adapters: [tomcat8(credentialsId: 'tomcatcredentials', path: '', url: 'http://3.109.186.143:8080')], contextPath: 'javaapp', war: '**/**.war'
      }
    }
  }
}
