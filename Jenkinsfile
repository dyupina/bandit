pipeline {
    agent any

    stages {
        
        stage('SCM') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script 
                {
                    def scannerHome = tool 'SonarScanner';
                    withSonarQubeEnv() {
                      bat "${scannerHome}/bin/sonar-scanner -D\"sonar.projectKey=Bandit\""                        
                    }
                }
            }
        }
        stage('Bandit Analysis') {
            steps {
                bat "bandit -r ./ > bandit_result.txt"
            }
        }        
    }
}
