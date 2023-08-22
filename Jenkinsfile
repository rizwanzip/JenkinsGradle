pipeline {
      agent any
      stages {
            stage('Track Build Application') {
                  steps {
                        echo '<<<Starting Build>>>'
						//build job: 'TrackApp-Build'
					//	bat  'gradlew clean build test'						
                        echo '<<<End Build>>>'
                  }
				   post {
						success{
								echo '<<<Archiving the Aritifact>>>'
						//		archiveArtifacts artifacts: '**/*.war'
							}
						}
				}
			stage('Create Tomcat Docker Image'){
                steps {
					echo '<<<Starting Docker Image 2>>>'
                    //bat "docker build . -t tomcatsamplewebapp:${env.BUILD_ID}"
					bat "gradlew bootBuildImage --imageName=com.centegy.global --builder=paketobuildpacks/builder:tiny  "
					 echo '<<<End Docker Image>>>'
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