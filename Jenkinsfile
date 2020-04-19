node {

	stage('preparation'){
	   checkout scm
	   sh "git rev-parse --short HEAD > .git/commit-id"
	   commit-id = readFile('.git/commit-id').trim()
    }
	
	stage('preparation pulling source'){
	 scm {
        git('git://github.com/dinakarsvin/test-airflow.git') {  node -> // is hudson.plugins.git.GitSCM
            node / gitConfigName('DSL Astro User')
            node / gitConfigEmail('jenkins-dsl@dina.com')
         }
	   }
	}
	stage('Login into registry'){
	  steps{
	    sh 'docker login registry.gcp0001.us-east4.astronomer.io -u _ -p 60e33bcc6e96c093efe4d210b1d6f7b3'
	  }
    }
	
	stage('Build'){
	  steps{
	    sh 'docker build -t registry.gcp0001.us-east4.astronomer.io/elementary-flyby-8509/airflow:ci-5'
	  }
    }
	
	stage('Deploy'){
	  steps{
	    sh 'docker push registry.gcp0001.us-east4.astronomer.io/elementary-flyby-8509/airflow:ci-5'
	  }
    }

}







