pipeline {
 agent { label 'FXG-SCM-DEV' } 
tools {
    maven 'M3'
  }
    stages {
	
	stage('Checkout_from_SCM') {	
	
	steps {
		
      emailext body: 'Please be waita !!!. Go to ${JOB_URL}/workflow-stage/ and see the status', subject: 'Congratulations !!! your Unit test cases are on the way', to: 's@1fedex.com'
	  
      checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'githup', url: 'https://github.com/sankarsingh/springboot5.git']]])

      }	
	}

	 stage('Build_CODE') {
		steps {
		       echo '##############Build the the code -Started###########'
			   bat('mvn -B -DskipTests clean package')
		      echo '##############Build the the code -completed###########'
		     }
			 }
		 
		 
  }

}
