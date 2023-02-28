pipeline {
	agent {
	label {
		label ('built-in')
		customWorkspace "/mnt/23Q1"
	}
	}
		stages {
			stage ('install docker') {
				steps {
					sh 'yum install docker git -y'
					sh 'systemctl start docker'
				}
			}
			stage ('deploy to 23Q1') {
				steps {
					sh 'rm -rf /mnt/23Q1/*'
					sh 'git clone https://github.com/Shivani5078/docker.git -b 23Q1'
					sh 'chmod 777 /mnt/23Q1/docker/index.html'
					sh 'docker run -itdp 80:80 --name 23Q1 httpd'
					sh 'docker cp /mnt/23Q1/docker/index.html 23Q1:/usr/local/apache2/htdocs'
				}
			}

			stage ('deploy to 23Q2') {
				steps {
					dir ('/mnt/23Q2') {
					sh 'rm -rf /mnt/23Q2/*'
					sh 'git clone https://github.com/Shivani5078/docker.git -b 23Q2'
					sh 'chmod 777 /mnt/23Q2/docker/index.html'
					sh 'docker run -itdp 90:80 --name 23Q2 httpd'
					sh 'docker cp /mnt/23Q2/docker/index.html 23Q1:/usr/local/apache2/htdocs'
				}
			}
			}
			stage ('deploy to 23Q3') {
				steps {
					dir ('/mnt/23Q3') {
					sh 'rm -rf /mnt/23Q3/*'
					sh 'git clone https://github.com/Shivani5078/docker.git -b 23Q3'
					sh 'chmod 777 /mnt/23Q3/docker/index.html'
					sh 'docker run -itdp 81:80 --name 23Q3 httpd'
					sh 'docker cp /mnt/23Q3/docker/index.html 23Q3:/usr/local/apache2/htdocs'
				}
			}
			}				
		}
}
