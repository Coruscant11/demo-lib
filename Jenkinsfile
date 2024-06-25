pipeline {
	agent any
	tools {nodejs "NodeJS 22"}
	stages {
	    stage('Prepare'){
	        sh 'npm version patch'
	    }
	    stage('Build'){
	        sh 'npm install'
	    }
	    stage('Publish'){
	        // TOP SECURITY : we PUBLISH only if we are in a main branch
	        if (env["CHANGE_ID"] != null){
	            sh 'npm version --no-git-tag-version'
	            sh 'npm publish'
	        }
	    }
	}
}
