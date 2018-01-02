pipeline {
    agent any
    tools {
        maven 'Maven 3.5.2'
        jdk 'jdk1.8.0_151'
    }
    stages {
        
        stage ('Build') {
            steps {
            bat 'mvn install'
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
        stage('SonarQube analysis') {
      tools {
        sonarQube 'sonar-runner-2.4'
      }
      steps {
        withSonarQubeEnv('SonarQube Scanner') {
          bat 'sonar-scanner'
        }
      }
    }
        
}
    }
