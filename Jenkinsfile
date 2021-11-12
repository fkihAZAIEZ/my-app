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
  		    sh "ansible-playbook ansible/build.yml -i ansible/inventory/hosts.yml"
			   }
		   }
	     }
   }
   }
