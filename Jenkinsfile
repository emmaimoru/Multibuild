pipeline{
	agent any
	stages{
		stage('version-control'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'ad', url: 'https://github.com/emmaimoru/Multibuild.git']]])
			}
		}
		stage('parallel-job'){
			parallel{
				stage('sub-job1'){
					steps{
						echo 'action1'
					}
				}
				stage('sub-job2'){
					steps{
						echo 'action2'
					}
				}
			}
		}
		stage('codebuild'){
			when{
				branch 'develop'
			steps{
				sh 'cat /etc/passwd'
			}
		}	
	}
}
