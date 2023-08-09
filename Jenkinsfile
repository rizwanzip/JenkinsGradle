pipeline {
      agent any
      stages {
            stage('Gradle Build Application') {
                  steps {
                        echo '<<<Starting Build>>>'
						bat  'gradlew clean build test'						
                        echo '<<<End Build>>>'
                  }
            }
            stage('Test') {
                  steps {
                        echo 'Building Sample Gradle Project'
                  }
            }
            stage('Deploy') {
                  steps {
                        echo "Deploying in Staging Area"
                  }
            }
            stage('Deploy Production') {
                  steps {
                        echo "Deploying in Production Area"
                  }
            }
      }
}