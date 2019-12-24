pipeline {
	agent any 
	stages {
		stage ('Git-Checkout') {
			steps {
					echo "Source code is being checked out...... at %date% : %time%";
					git "https://github.com/manoj-sakkarwal/Pipeline_Script.git";
			}
		}
		stage ('Build') {
			steps {
					bat label: '', script: 'Build.bat';
					echo "Build Stage Passed Successfully !!";
			}
		}
		stage ('Unit-Test') {
			steps {
					bat label: '', script: 'Test.bat';
					echo "Unit-Test Stage Passed Successfully !!";
			}
		}
		stage ('Quality-Gate') {
			steps {
					bat label: '', script: 'Quality.bat';
					echo "Quality-Gate Stage Passed Successfully !!";
			}
		}
		stage ('Deploy') {
			steps {
					bat label: '', script: 'Deploy.bat';
					echo "Deploy Stage Passed Successfully !!";
			}
		}
	}
    post {
		always {
				echo "This will always run"
		}
		success {
				echo "This will run only if successful"
		}		
		failure {
				echo "This will run only if failed"
		}
		unstable {
				echo "This will run only if the run was marked unstable"
		}
		changed {
				echo "This will run only if the state of the pipeline has changed"
				echo "For example, if the Pipeline was previously failing but is now successful"
		}
	}
}
