pipeline {
    agent {docker {image 'node:lts-slim'}}
	tools { 
      maven 'MAVEN_HOME' 
      jdk 'JAVA_HOME' 
    }

    stages{
			stage('Build'){
				steps{
					sh 'mvn --version'
					echo 'Build'
				}
			}
			stage('Test'){
				steps{
					echo 'Test'
				}
			}
			stage('Deploy'){
				steps{
					echo 'Deploy'
				}
			}
		}
		post {
			always {
				echo 'I am always'
			}
			success {
				echo 'I am success'
			}
			failure{
				echo 'I run when I am failure'
			} 
		}
}