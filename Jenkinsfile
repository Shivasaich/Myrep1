node {
    def mvnHome
    stage('Preparation') { git branch: 'newbranch', credentialsId: 'af760c75-67fc-4b21-8699-048a04bbda3f', url: 'https://github.com/Shivasaich/Myrep1.git'
    }
	
    stage('Build') {sh '''export M2_HOME=/usr/local/maven
                          export M2=$M2_HOME/bin
                          PATH=$M2:$PATH'''
	    
       sh 'mvn clean install verify'
    }
    stage(sonarqube) {withSonarQubeEnv(credentialsId: 'b24b6246-a33a-4bc1-a923-ed2d1746bcdd')
    // some block
}
    
	stage( Deploy) {deploy adapters: [tomcat9(credentialsId: 'eadc7c18-ba7f-4fc3-9b29-0ed420fbf828', path: '', url: 'http://192.168.33.10:8083')], contextPath: 'WAR/EAR', war: '**/*.war'
	}
	}
	
