pipeline {
    agent {
	label 'Windows_Node'
	}
    stages {
	
	stage('Non-Parallel Stage') {
	    agent {
                        label "master"
                }
        steps {
                echo 'This stage will be executed first'
                }
        }

	
        stage('Run Tests') {
            parallel {
                stage('Test On Windows') {
                    agent {
                        label "Windows_Node"
                    }
                    steps {
                        echo "Task1 on Agent"
                    }
                    
                }
                stage('Test On Master') {
                    agent {
                        label "master"
                    }
                    steps {
						echo "Task1 on Master"
					}
                }
            }
        }

    
 	
	stage('Git-Checkout') {
	    
             steps {
                echo "Checking out from Git Repo";
                git 'https://github.com/simplilearn-github/Pipeline_Script.git'
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
