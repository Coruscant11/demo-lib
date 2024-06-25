pipeline {
	agent any
	tools {nodejs "NodeJS 22"}
	stages {
	    stage('Prepare'){
		    steps {
		    	withCredentials([string(credentialsId: 'registry', variable: 'token')]) {
			    	sh 'ls -la'
			    	sh "echo //10.224.0.1:4873/:_authToken=$token} >> .npmrc"
		        	sh 'npm version patch --no-git-tag-version'
		      		sh 'npm whoami'
		      	}
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
	        			sh 'npm publish --registry "http://10.224.0.1:4873/"'
	        		} else {
	        			echo 'nothing to do'
	        		}
	        	}
	        }
	    }
	}
}
