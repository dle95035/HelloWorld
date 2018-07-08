
@Library('Utilities@master')  
import static org.conf.Utilities.* 

node ('worker_node2') { 
    
    def gradleHome
    
    stage('Source') { 
        git 'https://github.com/dle95035/HelloWorld.git' 
    } 
    
    //stage('Build') { 
    //    gradleHome = tool 'gradle32' 
    //    sh  "'${gradleHome}/bin/gradle' build" 
    //} 
    stage('Build') { 
        gbuild this, 'clean build' 
   } 
 
	stage ('Verify') { 
		def verifyCall = load("/root/repos/library/src/verify.groovy") 
        verifyCall("Please Verify the build") 
    } 
} 