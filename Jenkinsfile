pipeline {
      agent any
      stages {
            stage('Track Build Application') {
                  steps {
                        echo '<<<Starting Build>>>'
						bat 'gradlew.bat build test'  					
                        echo '<<<End Build>>>'
                  }
				  post {
						success {
							echo "Now Archiving the Artifacts...."
							archiveArtifacts artifacts: '**/*.war'
						}
					}				  
				  
            }
            stage('Track Deploy in Staging Envoirnment') {
                  steps {                        
						echo '<<<Starting Staging Deployment: copyArtifacts>>>'
						copyArtifacts fingerprintArtifacts: true, projectName: 'MyBuildJob', selector: upstream()
										
                        echo '<<<End Staging Deployment>>>'
                  }
            }
            
      }
}