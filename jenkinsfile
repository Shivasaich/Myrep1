node {
    def mvnHome
    stage('Git checkout') {
	 git branch: 'devops', credentialsId: 'af760c75-67fc-4b21-8699-048a04bbda3f', url: 'https://github.com/Shivasaich/Myrep1.git'
    }
    stage('Build') {
       sh 'mvn validate compile test package verify install'
    }
    stage('Email notification') {
        emailext body: 'sample_pipeline_job2', subject: 'Build has triggered', to: 'shivasaichinthala0@gmail.com'
    }
	stage ('Deploy') {
	deploy adapters: [tomcat9(credentialsId: 'eadc7c18-ba7f-4fc3-9b29-0ed420fbf828', path: '', url: 'http://192.168.33.10:8083')], contextPath: 'WAR.EAR', war: '/*war'
	}
}
