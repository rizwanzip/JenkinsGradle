pipeline {
      agent any
      stages {
            stage('Track Build Application') {
                  steps {
                        echo '<<<Starting Build>>>'
						//build job: 'TrackApp-Build'
						bat  'gradlew clean buildc test'						
                        echo '<<<End Build>>>'
                  }
				post {
                success {
                    echo 'Sending test success email..'
                    script{
				    emailext(
				    	from: 'rizwan.ahmed@centegytechnologies.com',
			            	body: 'Success',			            	
			            	mimeType: 'text/html',
			            	subject: '${DEFAULT_SUBJECT}',
			            	to: 'rizwan.ahmed@centegytechnologies.com'
			    		)
                    }
                    echo 'Email sent..'
                }
                failure {
                    echo 'Sending test failure email..'
                    script{
				    emailext(
				    	from: 'rizwan.ahmed@centegytechnologies.com',
			            	body: 'Failure',
			            	mimeType: 'text/html',
			            	subject: '${DEFAULT_SUBJECT}',
			            	to: 'rizwan.ahmed@centegytechnologies.com'
			    		)
                    }
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