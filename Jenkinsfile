pipeline {
      agent any
      stages {
            stage('Track Build Application') {
                  steps {
                        echo '<<<Starting Build>>>'
						//build job: 'TrackApp-Build'
						//bat  'gradlew clean buildc test'						
                        echo '<<<End Build>>>'
                  }
				  post {
                success {
                    echo 'Sending test success email..'
                    script{
				    emailext(
				    	from: 'rizwan.ahmed@centegytechnologies.com',
			            	body: 'hello fawad',			            	
			            	mimeType: 'text/html',
			            	subject: '${DEFAULT_SUBJECT}',
			            	to: 'rizwan.ahmed@centegytechnologies.com'
			    		)
                    }
                    echo 'Email sent..'
                }                
            }
							  

            }
			stage('Track Test Application') {
				steps {
					echo "....Testing In-Progress...."
				}
			}
            stage('Track Deploy in Staging Envoirnment') {
                  steps {                        
						echo '<<<Starting Staging Deployment>>>'
					//	build job: 'TrackApp-Staging-Deployment'						
                        echo '<<<End Staging Deployment>>>'
                  }
            }
		}
	}