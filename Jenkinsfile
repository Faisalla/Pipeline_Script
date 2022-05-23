
pipeline {
    
	agent {
	label 'Windows_Node'
	}

    stages {
	
	stage('Git-Checkout') {
	    
             steps {
                echo "Checking out from Git Repo";
                git 'https://github.com/Faisalla/Pipeline_Script.git'
                }
        }
	stage('Build') {
	    
             steps {
                echo "Building the Checkout Project!";
                bat 'Build.bat'
                }
        }
	stage('Unit-Test') {
	    
             steps {
                echo "Running JUnit Tests!";
                bat 'Unit.bat'
                }
        }

	stage('Quality-Gate') {
	    
             steps {
                echo "Verifying the Quality Gates!";
                bat 'Quality.bat'
                }
        }

	stage('Deploy') {
	    
             steps {
                echo "Deploying to stage Environment for more tests!";
                bat 'Deploy.bat'
                }
        }
}

}
