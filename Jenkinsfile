pipeline {
      agent any
      stages {
            stage('Gradle Build Application') {
                  steps {
                        echo '<<<Starting Build>>>'
						bat  'gradlew clean build test'						
                        echo '<<<End Build>>>'
                  }
				  post {
						success{
								echo '<<<Archiving the Aritifact>>>'
								archiveArtifacts artifacts: '**/*.war'
							}
						}
				  
            }
            stage('Deploy in Staging Envoirnment') {
                  steps {                        
						build job: 'DeployApplicationStagingEnv'
                  }
            }
            
      }
}