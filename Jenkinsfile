node {
    def mvnHome
    stage('Preparation') { git branch: 'newbranch', credentialsId: 'af760c75-67fc-4b21-8699-048a04bbda3f', url: 'https://github.com/Shivasaich/Myrep1.git'
    }
    stage('Build') {
       sh 'mvn clean package'
    }
    stage('Results') {
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts 'target/*.jar'
    }
	stage (Email) { emailext body: 'pipeline_jon', subject: 'Job is successfull', to: 'shivasaichinthala.0@gmail.com'
	}
	stage (Deploy) {deploy adapters: [tomcat9(credentialsId: 'eadc7c18-ba7f-4fc3-9b29-0ed420fbf828', path: '', url: 'http://192.168.33.10:8083')], contextPath: 'WAR/EAR', war: '*/*.war'
	}
	stage (sonarqube) {sh 'sonar:sonar'}
}
