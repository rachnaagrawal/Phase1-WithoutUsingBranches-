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
			dir('D:\CloneDIR') {
    			git branch: 'master', credentialsId: '3d5cdb37-6e90-465b-9b1d-527ae99e152d', url: 'https://github.com/Ritik180/Phase1-WithoutUsingBranches-.git'
				}
			}
		}
	}
}