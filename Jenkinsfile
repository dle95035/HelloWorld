
@Library('Utilities@master')  
import static org.conf.Utilities.* 

node ('worker_node2') { 
    
    def gradleHome
    
	try {
	
		// get source.
		stage('Source') { 
			git 'https://github.com/dle95035/HelloWorld.git' 
		} 
		
		// use gbuild from global shared library. 
		stage('Build') { 
			gbuild this, 'clean build' 
		}	 
	
		// use local shared libary.
		stage ('Verify') { 
			def verifyCall = load("/root/repos/library/src/verify.groovy") 
			
			// get user input with timeout of 5 seconds.
			timeout(time: 5, unit: 'SECONDS') {
				verifyCall("Please Verify the build") 
			}
		} 
	}
	catch (err) { 
		echo "Caught: ${err}"       
	} 
	stage ('Notify') { 
		//mailUser(<email address in single quotes>,"Finished") 
		echo "==> finished."
	} 
} 