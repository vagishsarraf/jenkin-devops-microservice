pipeline {
    agent {docker {image 'maven:3.9.5-amazoncorretto-8-debian-bookworm'}}
    stages{
			stage('Build'){
				steps{
				    sh 'echo $PATH'
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