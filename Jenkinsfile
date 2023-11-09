node {
	stage('prepare') {
		git branch: 'main', poll: false, url: 'https://github.com/RiteshDevOpsTrainer/restro.git'
	}
	
	stage('build') {
		def mvnHome = tool 'MAVEN'
		withEnv(["MVN_HOME=$mvnHome"]){
			sh '"$MVN_HOME/bin/mvn" clean compile package'
		}
	}
	
	stage('deploy') {
		deploy adapters: [tomcat9(credentialsId: 'a22e1a53-ab62-43de-a140-52461daa662b', path: '', url: 'http://3.111.32.10:8080/')], contextPath: null, war: '**/*.war'
	}

}
