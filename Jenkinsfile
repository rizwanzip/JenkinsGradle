pipeline {
      agent any
	  parameters {
        string(name: 'NAME', description: 'Please tell me your name')
        choice(name: 'GENDER', choices: ['Male', 'Female'], description: 'Choose Gender')
    }
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
						echo '<<<Starting Staging Deployment: copyArtifacts5>>>'
						
						copyArtifacts(projectName: "$JOB_NAME", selector: lastSuccessful(stable: true), optional: true)
										
                        echo '<<<End Staging Deployment>>>'
                  }
            }
            
      }
}