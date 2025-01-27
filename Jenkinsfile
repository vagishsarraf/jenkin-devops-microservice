pipeline {
    agent any
    stages{
			stage('Build'){
				steps{
				    sh 'echo $PATH'
					sh 'mvn --version'
					echo '-*-*--*-*--*-*-Build Info-*-*--*-*--*-*-'
					echo 'BUILD - $env.BUILD_ID'
					echo 'BUILD Number - $env.BUILD_NUMBER'
					echo 'JAVA_HOME - $env.JAVA_HOME'
					echo 'JOB_NAME - $env.JOB_NAME'
					echo '-*-*--*-*--*-*-Build Info-*-*--*-*--*-*-'
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
			stage('Package'){
				steps{
					sh "mvn package -DskipTest"
				}
			}
			stage('Build Docker Image'){
				steps{
					script{
						dockerImage = docker.Build("vagishsarrafib/dockerlearning:$env.BUILD_ID")
					}
				}
			}
			stage('Push Docker Image'){
				steps{
					script{
						withDockerRegistry(credentialsId: 'Dockerhub_pass', url: 'hub.docker.com'){
						dockerImage.push('latest');
					}
					}
		}
	}}
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