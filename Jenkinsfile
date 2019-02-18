pipeline {

 agent { label 'FXG-SCM-DEV' } 

    stages {
	
	stage('Checkout_from_SCM') {	
	
	steps {

      emailext body: 'Please be waita !!!. Go to ${JOB_URL}/workflow-stage/ and see the status', subject: 'Congratulations !!! your Unit test cases are on the way', to: 'ajay.kakumanu.osv@fedex.com'
      checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'githup', url: 'https://github.com/sankarsingh/springboot5.git']]])

        }
	
	}
	
	
	 stage('Set_Enviroment') {
		steps {
		    sh '''
                ls -la
				export M2_HOME=/home/cmbuild3/CMUTILITIES/apache-maven-3.3.9
				export M2=$M2_HOME/bin
				export PATH=$PATH:$M2_HOME:$M2:$JAVA_HOME:$JAVA_HOME\bin
                echo "M2_HOME = ${M2_HOME}"
				export TZ=EST
				export ORACLE_SID=FXGPLDB
				export ORACLE_HOME=/opt/fedex/scm/product/10.2.0.4
				export MQSI_EMPTY_DB_CACHE=Y
	            export PATH=$PATH:$M2_HOME:$M2:$ORACLE_HOME:$ORACLE_HOME/lib:$ORACLE_HOME/bin
			    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$ORACLE_HOME:$ORACLE_HOME/lib:$ORACLE_HOME/rdbms/lib:$ORACLE_HOME/bin
				echo $PATH
				echo $JAVA_HOME
				mvn -version
		    ''' 
	       }
	}
	
	 stage('Build_CODE') {
		steps {
		    echo '##############Build the the code -Started###########'
			
		   mvn clean package
		      echo '##############Build the the code -completed###########'
		     }
			 }
		 
		 
  }

}
