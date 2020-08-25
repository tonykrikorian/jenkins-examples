pipeline{
    agent any
    stages{
        stage("build"){
            steps{
                echo "Building ${BRANCH_NAME}"
                echo "Building application"
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
                    s3Upload(file:'index.html', bucket:'elasticbeanstalk-us-east-2-321304165861', pathStyleAccessEnabled :true,payloadSigningEnabled :true)
                }
            }
        }
    }
}