pipeline {
  agent none
  stages {
    stage('Run Tests') {
      parallel {
        stage('Test On maitre') {
          agent {
            label "maitre"
          }
          steps {
	  		    script {
              for (int i = 0; i < 10; ++i) {
                echo "Bonjour $i"
		  				  sleep 1
              }
						}
          }
          post {
            always {
              echo 'Stage Windows terminé'
            }
          }
        }
        stage('Test On Linux') {
				  when {
            branch "master"
          } 
          agent {
            label "Linux"
          }
          steps {
					  sleep 10;
            echo "Il s'agit build ${BUILD_NUMBER}"
          }
          post {
            always {
              echo 'Stage Linux terminé'
            }
          }
        }
      }
    }
  }
}
