pipeline {
    agent any
   
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven"
    }

    stages {
        stage('Gitcheckout') {
            steps {
                git branch: 'main', credentialsId: 'gitcredinti', url: 'https://github.com/reddivani/WebAppExample.git'
            }
     }
     stage('build') {
            steps {
             bat "mvn clean install"
            }
        }
        stage('deploy') {
            steps {
             deploy adapters: [tomcat8(credentialsId: 'Tomcat-cred2', path: '', url: 'http://localhost:8000/')], contextPath: ' webAppExample', war: '**/*.war'
            }
        }
      stage('codeQuality') {
            steps {
             bat "mvn sonar:sonar"
            }
        }  
    }
}
