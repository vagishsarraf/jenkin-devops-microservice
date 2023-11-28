pipeline {
    agent {docker {image 'maven:3.9.5-amazoncorretto-8-debian-bookworm'}}
    stages{
		stage('Example Username/Password') {
            environment {
				dockerHome = tool 'myDocker'
				mavenHome = tool 'myMaven'
				PATH = '$dockerHome/bin:$mavenHome/bin:$PATH'
            }
            steps {
                sh 'echo "Docker home is $dockerHome"'
                sh 'echo "Maven Home is $mavenHome"'
            }
        }
			stage('Build'){
				steps{
				    sh 'echo $PATH'
					sh 'mvn --version'
					echo '-*-*--*-*--*-*-Build Info-*-*--*-*--*-*-'
					echo 'BUILD - $env.BUILD_ID'
					echo 'BUILD Number - $env.BUILD_NUMBER'
					echo 'JAVA_HOME - $env.JAVA_HOME'
					echo 'JOB_NAME - $env.JOB_NAME'
				}
			}
			stage('clean'){
				steps{
					sh 'mvn clean'
				}
			}
			stage('Compile'){
				steps{
					sh 'mvn compile'
				}
			}
			stage('Test'){
				steps{
					sh 'mvn test'
				}
			}
			stage('Integration Test'){
				steps{
					sh 'mvn failsafe:integration-test failsafe:verify'
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