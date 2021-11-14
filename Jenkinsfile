pipeline 
{
  agent any
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            credentialsId: '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',
                            url: 'https://github.com/fkihAZAIEZ/my-app.git']]])
                }
            }
        }
        stage('Build'){
	     steps{
                     script{
                          sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/hosts.yml"
			   }
		   }
	     }
        stage('docker')
{
             steps {
                     script{
                          sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml "
                                }
                        }
  }

        stage('dockerHub')
 {           
             steps{
                script{
                    sh "ansible-playbook ansible/register.yml -i Ansible/inventory/host.yml"
                }
            }
        }      

   }
   }
