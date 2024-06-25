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
	        	script {
					if (env["CHANGE_ID"] == null){
	        			sh 'npm adduser test test'					
	            		sh 'npm publish'
	        		} else {
	        			echo 'nothing to do'
	        		}
	        	}
	        }
	    }
	}
}
