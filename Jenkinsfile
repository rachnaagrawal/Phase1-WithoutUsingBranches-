pipeline{
    agent any
    stages{
        stage('STEP 3'){
            steps{
                echo "${WORKSPACE}"
               
            }
        }
        stage('Clone'){
            steps{
            dir("D:\\CloneDIR\\version_$BUILD_ID") {
                git branch: 'master', credentialsId: 'gitlogin', url: 'https://github.com/bharatbhallaCoder/Phase1-WithoutUsingBranches-.git'
				}
                echo "$BUILD_ID"
            }
        }
        stage('BootStrap with TargetConfiguration'){
            steps{
                configFileProvider([configFile(fileId: 'dev-sys', targetLocation: "${WORKSPACE}", variable: 'dfvdf')]) {
                    // some block
                }
            }
        }
        stage('Set Version'){
            steps{        
                    bat "mvn versions:set -DnewVersion=1.0.${BUILD_ID} -f pom.xml"
                                 
            }
        }
        stage('Munit Test'){
            steps{
                bat "mvn clean test"
            }       
        }
		stage('build'){
			steps{
			bat 'del temp.txt'
            bat 'curl -d "username=bharatbhalla&password=Boardsarecoming@1" https://anypoint.mulesoft.com/accounts/login >> temp.txt '
            def ref=readJSON file: 'temp.txt'
            echo "hello"
            echo "${ref.access_token}"
			bat "mvn deploy -Dpassword=${ref.access_token} -DrepositoryId=ExchangeRepository " 
			}
 
        }
	}
       
}