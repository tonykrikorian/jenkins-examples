pipeline{
    agent any
    stages{
        stage("build"){
            steps{
                echo "Building ${BRANCH_NAME}"
                echo "Building application"
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
            }

        }
        stage("deploy"){
            steps{
                echo "Deploying ${BRANCH_NAME}"
                echo "Deploying application"
                withAWS(region: 'us-west-2',credentials:'AWS_DEVOPS'){
                    echo "Login in AWS"
                    echo "Uploading to S3"
                    s3Upload(file:'index.html', bucket:'jenkins-bucket-tony', pathStyleAccessEnabled :true,payloadSigningEnabled :true)
                }
            }
        }
    }
}