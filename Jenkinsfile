pipeline {
    agent any

    environment {
        JAVA_HOME = "/usr/lib/jvm/java-17-amazon-corretto"
        PATH = "${JAVA_HOME}/bin:${PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/shobna111/your-java-repo.git'
            }
        }

        stage('Compile') {
            steps {
                sh '''
                    mkdir -p out
                    javac -d out src/*.java
                '''
            }
        }

        stage('Run') {
            steps {
                sh 'java -cp out Main'
            }
        }
    }

    post {
        success {
            echo 'Build and run completed successfully.'
        }
        failure {
            echo 'Something went wrong.'
        }
    }
}
