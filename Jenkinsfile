pipeline{
	any agent{
               
		stages {
                     stage ('Clone Git repo'){
                        steps{
			    sh git branch: 'main' , url: 'https://github.com/abhishek-7980/docker-assigement-3.git'
			  }
			}
		
		      stage ('Delete Old Container'){
                         steps{
                            sh 'docker rm -f c1 c2 c3 || true'         
                           }
			}
			stage ( 'Volume Create for Container'){
			  steps{
				sh 'docker volume create Q1-container '
			    }	
			}
			stage ('Deploy 2026-Q1'){
			  steps{
			    sh 'git checkout 2026-Q1'
			    sh 'docker run -dp 80:80 -v Q1-container:/usr/local/apache2/htdocs --name c1 httpd'
			    sh 'docker cp index.html c1:/usr/local/apace2/htdocs/index.html'
			    sh 'docker exec chomd 777 -R /usr/local/apace2/htdocs/index.html'
				}
			}
			stage ('Volume Create for Container')	{
			  steps {
			     sh 'docker volume create Q2-container'
			    }
			}
			stage ('Deploy 2026-Q2'){
			  steps {
			    sh 'docker run -dp 90:80 -v Q2-container:/usr/local/apache2/htdocs --name c2 httpd '
			    sh 'docker cp index.html  c2:/usr/local/apache2/htdocs/index.html'			   
			    sh 'docker exec chmod 777 -R /usr/local/apache2/htdocs/index.html'	
			    }
			}
			stage ('Volume Create for Container')	{
			  steps {
			     sh 'docker volume create Q3-container'
			    }
			}

			stage ('Deploy 2026-Q3'){
			  steps {
  			     sh 'docker run -dp 9080:80 -v Q2-container:/usr/local/apache2/htdocs --name c3 httpd '
			     sh 'docker cp index.html c3:/usr/lib/apache2/htdocs/index.html'
			     sh 'docker exec chmod 777 -R c3:/usr/lib/apache2/htdocs/index.html'
			  }
			}							
          }

    } 
}
