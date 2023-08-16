pipeline {
      agent any
      stages {
            stage('Track Build Application') {
                  steps {
                        echo '<<<Starting Build>>>'
						build job: 'TrackApp-Build'						
                        echo '<<<End Build>>>'
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
						build job: 'TrackApp-Staging-Deployment'						
                        echo '<<<End Staging Deployment>>>'
                  }
            }
		}
	}