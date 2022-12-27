node {
    def mvnHome
    stage('Preparation') { git branch: 'newbranch', credentialsId: 'af760c75-67fc-4b21-8699-048a04bbda3f', url: 'https://github.com/Shivasaich/Myrep1.git'
    }
    stage('Build') {
       sh 'mvn clean install verify'
    }
	stage (Email) {emailext body: 'Pipeline_job', subject: 'Build success', to: 'shivasaichinthala.0@gmail.com'
	}
}
	
