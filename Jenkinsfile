pipeline {
	agent any
	tools {nodejs "NodeJS 22"}
	stages {
	    stage('Prepare'){
		    steps {
		    	withCredentials([string(credentialsId: 'registry', variable: 'token')]) {
			    	sh "echo //localhost:4873/:_authToken=$token} >> .npmrc"
					sh 'npm version patch --no-git-tag-version'
		      	}
		    }
	    }
	    stage('Build'){
		    steps {
	        	sh 'npm install'
		    }
	    }
	    stage('Publish'){
	        // TOP SECURITY : we PUBLISH prod version only if we are in a main branch
	        steps {
	        	script {
					if (env["CHANGE_ID"] == null){
	        			sh 'npm publish --registry "http://localhost:4873/"'
	        		} else {
						echo 'Nothing to do'
	        		}
	        	}
	        }
	    }
	}
}
