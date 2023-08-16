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
				          post{
								success{
								 script{
									emailext to: "rizwan.ahmed@centegytechnologies.com",
									subject: '${DEFAULT_SUBJECT}',
									//body: "Test-Success",
									 body: "${currentBuild.currentResult}: Job ${env.JOB_NAME}\nMore Info can be found here: ${env.BUILD_URL}",
									mimeType: 'text/html',
									attachLog: true
									}
								}
								failure {                    
									script{
									emailext(
											to: 'rizwan.ahmed@centegytechnologies.com',
											//body: 'Failure',
											 body: "${currentBuild.currentResult}: Job ${env.JOB_NAME}\nMore Info can be found here: ${env.BUILD_URL}",
											mimeType: 'text/html',
											subject: '${DEFAULT_SUBJECT}',
											attachLog: true											
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