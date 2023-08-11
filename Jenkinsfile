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
								archiveArtifacts artifact: '**/*.jar'
							}
						}
				  
            }
            stage('Deploy in Staging Envoirnment') {
                  steps {
                        echo '<<<Deploy in Staging Envoirnment>>>'
						build job: 'DeployApplicationStagingEnv'
                  }
            }
            stage('Deploy Production') {
                  steps {
                        echo "Deploying in Production Area"
                  }
            }
      }
}