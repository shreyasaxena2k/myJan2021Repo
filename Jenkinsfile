pipeline {
    agent any

    tools {
     maven 'Maven3'
    }
  
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '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', url: 'https://github.com/shreyasaxena2k/myJan2021Repo']]])
            }
        }
        
       stage ('Build') {
         steps {
              sh 'mvn clean install -f MyWebApp/pom.xml'
            }
        }
        
        stage ('Code Quality') {
        steps {
            withSonarQubeEnv('My_SonarQube') {
            sh 'mvn -f MyWebApp/pom.xml sonar:sonar'
            }
        }
      }   
    }
}
