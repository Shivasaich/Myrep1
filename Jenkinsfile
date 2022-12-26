node {
    def mvnHome
    stage('Preparation') { git branch: 'mavenjob', credentialsId: 'af760c75-67fc-4b21-8699-048a04bbda3f', url: 'https://github.com/Shivasaich/Myrep1.git'
    }
    stage('Build') {sh 'mvn clean package'
        
    }
    stage('Results') {
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts 'target/*.jar'
    }
}
