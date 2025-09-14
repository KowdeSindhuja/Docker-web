pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                echo "Build docker image "
                bat "docker build -t mypyhtonapp ."
            }
        }
        stage("Run") {
            steps {
                echo "Run application in docker container"
                bat "docker rm -f mycontainer||exit 0"
                bat "docker run -d -p 5000:5000 --name mycontainer mypythonapp"
            }
        }
    }
    post {
        success {
            echo "Pipeline completed successfully"
        }
        failure {
            echo "Pipeline failed. Please check the logs.."
        }
    }
}