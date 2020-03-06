properties([[$class: 'EnvInjectJobProperty', info: [loadFilesFromMaster: false, propertiesFilePath: "${WORKSPACE}\\dev-sys.properties", secureGroovyScript: [classpath: [], sandbox: false, script: '']], keepBuildVariables: true, keepJenkinsSystemVariables: true, on: true]])
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
				configFileProvider([configFile(fileId: 'dev-sys', targetLocation: "D:\\CloneDIR\\version_$BUILD_ID", variable: 'dfvdf')]) {
    				// some block
    				
    				echo "$dfvdf"
				}
			}
		}
	}
}