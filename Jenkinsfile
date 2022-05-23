
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


post {		
		always {
		echo 'This will always run'
		}

		success {
		echo 'This will run only if successful'
		}
		
		failure {
		    echo 'This will run only if failed'
		}
		
		unstable {
		    echo 'This will run only if the run was marked as unstable'
		}

		changed {
		    echo 'This will run only if the state of the pipeline has changed'
		    echo 'For example, if the Pipelline was previously failing but is now successful'
		}
	    }

	}
