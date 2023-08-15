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
						copyArtifacts fingerprintArtifacts: true, projectName: 'TrackApp-Build2', fingerprint: true, selector: lastCompleted()
						echo '<<<Starting Staging Deployment: deploy adapters>>>'
						deploy adapters: [tomcat9(url: 'http://localhost:8082',
							credentialsId: 'tomcat/123456')], 
							war: '**/*.war',
							contextPath: 'app7'						
										
                        echo '<<<End Staging Deployment>>>'
                  }
            }
            
      }
}