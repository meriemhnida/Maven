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
        
        stage('Sonarqube analysis') {
    steps {
    script {
             scannerHome = tool 'SonarScanner';
        }
     withSonarQubeEnv('SonarQube') {
       bat "${scannerHome}/bin/sonar-scanner.bat" 
    }

    } 
        }
        
}
    }
