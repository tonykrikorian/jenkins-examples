pipeline{
    agent any
    stages{
        stage("build"){
            steps{
                echo "Building ${BRANCH_NAME}"
                echo "Building application"
                nodejs('NodeJS'){
                    sh "npm install"
                    sh "npm run build"
                }
            }

        }
        stage("Lint HTML"){
            steps{
                sh "tidy -q -e *.html"
            }
        }
        stage("test"){
            steps{
                echo "Testing ${BRANCH_NAME}"
                echo "Testing application"
                nodejs('NodeJS'){
                    sh "npm test"
                }
            }

        }
        stage("deploy"){
            steps{
                echo "Deploying ${BRANCH_NAME}"
                echo "Deploying application"
                withAWS(region: 'us-west-2',credentials:'AWS_DEVOPS'){
                    echo "Login in AWS"
                    echo "Uploading to S3"
                    s3Upload(file:'build', bucket:'jenkins-bucket-tony', pathStyleAccessEnabled :true,payloadSigningEnabled :true,path:'jenkins-bucket-tony/react-app')
                }
            }
        }
    }
}