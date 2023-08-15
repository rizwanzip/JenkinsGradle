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
            stage('Track Deploy in Staging Envoirnment2') {
                  steps {                        
						echo '<<<Starting Staging Deployment: copyArtifacts>>>'
						
						copyArtifacts(projectName: "$JOB_NAME", selector: lastSuccessful(stable: true), optional: true)
						echo '<<<Starting Staging Deployment: deploy adapters>>>'
						deploy adapters: [tomcat9(url: 'http://localhost:8082',
							credentialsId: 'tomcat')], 
							war: '**/*.war',
							contextPath: 'app7'
										
                        echo '<<<End Staging Deployment>>>'
                  }
            }
            
      }
}