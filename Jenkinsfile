pipeline {
	agent any
	tools {nodejs "NodeJS 22"}
	stages {
	    stage('Prepare'){
		    steps {
	        	sh 'npm version patch --no-git-tag-version'
		    }
	    }
	    stage('Build'){
		    steps {
	        	sh 'npm install'
		    }
	    }
	    stage('Publish'){
	        // TOP SECURITY : we PUBLISH only if we are in a main branch
	        steps {
	      			sh 'npm publish --registry "http://10.224.0.1:4873/"'
	        	}
	    }
	}
}
