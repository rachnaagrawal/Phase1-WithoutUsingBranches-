pipeline{
    agent any
    stages{
        stage('Checkout'){
            steps{
                 checkout([$class: 'GitSCM',
          branches: [[name: "${env.branch}"]],
    doGenerateSubmoduleConfigurations: false,
    extensions: [[$class: 'CleanCheckout']],
    submoduleCfg: [],
    userRemoteConfigs: [[credentialsId: 'gitlogin', url: 'https://github.com/bharatbhallaCoder/Phase1-WithoutUsingBranches-.git']]
])
                echo "${WORKSPACE}"
               
            }
        }
        stage('Clone'){
            steps{
            dir("D:\\CloneDIR\\version_$BUILD_ID") {
                git branch: "${env.branch}", credentialsId: 'gitlogin', url: 'https://github.com/bharatbhallaCoder/Phase1-WithoutUsingBranches-.git'
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
            script{
				def ref=readJSON file: 'temp.txt'
           	 echo "hello"
            echo "${ref.access_token}"
			bat "mvn deploy -Dpassword=${ref.access_token} -DrepositoryId=ExchangeRepository " 
			}
			
			}
 
        }

		

	}
       
}