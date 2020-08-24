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
            }
        }
    }
}