stage('preparation pulling source'){
	   checkout scm
	   sh "git clone https://github.com/dinakarsvin/test-airflow.git"
	}
	stage('Login into registry'){
	  step{
	    sh 'docker login registry.gcp0001.us-east4.astronomer.io -u _ -p 60e33bcc6e96c093efe4d210b1d6f7b3'
	  }
    }
	
	stage('Build'){
	  step{
	    sh 'docker build -t registry.gcp0001.us-east4.astronomer.io/elementary-flyby-8509/airflow:ci-5'
	  }
    }
	
	stage('Deploy'){
	  step{
	    sh 'docker push registry.gcp0001.us-east4.astronomer.io/elementary-flyby-8509/airflow:ci-5'
	  }
    }
