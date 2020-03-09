node{
		stage('STEP 3'){
			
				echo "${WORKSPACE}"
				
			
		}
		stage('Clone'){
			
			dir("D:\\CloneDIR\\version_$BUILD_ID") {
    			git branch: 'master', credentialsId: '3d5cdb37-6e90-465b-9b1d-527ae99e152d', url: 'https://github.com/Ritik180/Phase1-WithoutUsingBranches-.git'
				}
				echo "$BUILD_ID"
			
		}
		stage('BootStrap with TargetConfiguration'){
			
				configFileProvider([configFile(fileId: 'dev-sys', targetLocation: "${WORKSPACE}", variable: 'dfvdf')]) {
    				// some block
				}
			
		}
		stage('Set Version'){
					
    				bat "mvn versions:set -DnewVersion=1.0.${BUILD_ID} -f pom.xml"  
				  				
			
		}
		stage('Munit Test'){
			
				bat "mvn clean test"
				
		}
		 stage('build'){
           
            bat 'del temp.txt'
            bat 'curl -d "username=bharatbhalla&password=Boardsarecoming@1" https://anypoint.mulesoft.com/accounts/login >> temp.txt '
            def ref=readJSON file: 'temp.txt'
            echo "hello"
            echo "${ref.access_token}"
			bat 'mvn deploy -Dusername=~~~Token~~~ -Dpassword="${ref.access_token}" -DrepositoryId=ExchangeRepository  '  
        }

	
}