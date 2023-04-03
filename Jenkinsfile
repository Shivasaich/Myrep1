pipeline {
     agent any
	 
	stages {
	    
		stage ('Git checkout') {
		   steps {
		   git branch: 'devops', credentialsId: 'af760c75-67fc-4b21-8699-048a04bbda3f', url: 'https://github.com/Shivasaich/Myrep1.git'
		   }
		   }
		stage ('Build') {
                   steps { dir ('devops') {
		   sh 'validate test compile package verify install'
		   }
		   }
		   }
		stage ('Email notification') {
		   steps {
            emailext body: '', subject: 'Build is suceess', to: 'shivasaichinthala0@gmail.com'
           }		   
		   }
		stage ('Deploy') {
                   steps {
            	deploy adapters: [tomcat9(credentialsId: 'eadc7c18-ba7f-4fc3-9b29-0ed420fbf828', path: '', url: 'http://192.168.33.10:8083')], contextPath: 'WAR.EAR', war: '/*war'

			}
			}
	}
}	
