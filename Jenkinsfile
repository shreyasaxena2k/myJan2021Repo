pipeline {
    agent any

    tools {
     maven 'Maven3'
    }
  
    stages {
        stage("Checkout") {
            steps {
                script {
                    git branch: 'master', credentialsId: 'github', url: 'https://github.com/shreyasaxena2k/myJan2021Repo';
                }
            }
        }
       stage ('Build') {
         steps {
              sh 'mvn clean install -f MyWebApp/pom.xml'
            }
        }
        
       stage ('Code Quality') {
         steps {
            withSonarQubeEnv('central-sonar-01') {
            sh 'mvn -f MyWebApp/pom.xml sonar:sonar'
            }
          }
       }   
    }
}
