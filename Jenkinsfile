pipeline{
    agent any
    tools{
        nodejs 'NodeJS'
    }
    stages{
        stage('CheckOutCode'){
            steps{
                git credentialsId: '984d435b-2abc-4527-8b9b-82293f145ff4', url: 'https://github.com/Devops-kamlesh/nodejs-app-mss.git'
            }
        }
        stage('Build'){
        steps{
            sh "npm install"
        }
        }
        stage('Execute SonarQube Report'){
            steps{
                sh "npm run sonar"
            }
        }
        stage('Upload Atrifact into Nexus'){
            steps{
                sh "npm publish --registry http://13.127.44.68:8081/repository/wallmart-npm-repo/"
            }
        }
        stage('Run Nodejs App'){
            steps{
                sh "chmod u+x ./scripts/runApp.sh"
                sh "./scripts/runApp.sh"
            }
        }
        
    }//end of stages
}//end of pipeline
