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
				          post{
								always{
									emailext to: "rizwan.ahmed@centegytechnologies.com",
									subject: "Test Email",
									body: "Test"
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