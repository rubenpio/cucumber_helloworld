pipeline {
    agent any
    
    stages {
        stage('Get Code') {
            steps {
                git branch: "master", url: 'https://github.com/rubenpio/cucumber_helloworld.git'
		bat 'dir'
                bat 'echo %WORKSPACE%'
            }
        }
        
        stage('Build&Test')
        {
            steps {
                catchError(buildResult: 'UNSTABLE', stageResult: 'FAILURE') {
                    bat '"C:\\Program Files\\Java\\apache-maven-3.9.6\\bin\\mvn" test'
                }
            }
        }
        
        stage('Results')
        {
            steps {
                cucumber fileIncludePattern: 'cucumber.json', jsonReportDirectory: 'target/', reportTitle: 'Cucumber Reports'
            }
        }
    }
}		
