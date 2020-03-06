properties([[$class: 'EnvInjectJobProperty', info: [loadFilesFromMaster: false, propertiesFilePath: "${env.WORKSPACE}\\dev-sys.properties", secureGroovyScript: [classpath: [], sandbox: false, script: '']], keepBuildVariables: true, keepJenkinsSystemVariables: true, on: true]])
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
    			git branch: 'master', credentialsId: '3d5cdb37-6e90-465b-9b1d-527ae99e152d', url: 'https://github.com/Ritik180/Phase1-WithoutUsingBranches-.git'
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
				configFileProvider([configFile(fileId: 'dev-sys', targetLocation: "${WORKSPACE}", variable: 'dfvdf')]) {
					bat "echo &echo.anypoint.version=1.0.${BUILD_ID} >> dev-sys.properties"
					echo "$dfvdf"
    				// some block
				}	
    				
			}
		}
		stage('Munit Test'){
			bat "mvn clean test"		
		}
	}
}