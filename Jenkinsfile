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
                        echo '<<<Deploy in Staging Envoirnment>>>'
						timeout(time:5, unit:'DAYS'){
                        input message:'Approve Staging Deployment?'
						}
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