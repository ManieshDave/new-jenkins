pipeline {
	agent {
		node {
			label 'ssh-node' 
			customWorkspace "/server/git/"
		}
	}
	stages ('Automation') {
		stage ('installing docker') {
			steps {
				sh '''
					yum install docker -y	
					systemctl start docker 
					systemctl enable docker
				'''
			}
		}
		stage ('Installing docker-compose') {
			steps {
				sh '''
					curl -L --fail https://github.com/docker/compose/releases/download/1.29.2/run.sh -o /usr/local/bin/docker-compose
					chmod +x /usr/local/bin/docker-compose
				'''
			}
		}
		stage ('Cloning docker-compose and building Image') {
			steps {
				sh '''
					git clone https://github.com/ManieshDave/docker-compose.git
					cd docker-compose && docker-compose up -d
				'''
			}
		}
	}
}
