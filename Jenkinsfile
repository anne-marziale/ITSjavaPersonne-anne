pipeline {
    agent any
    stages {
        stage('Clone repo') {
            steps {
                sh '''
                pwd
                rm -rf ITSjavaPersonne-anne
                git clone https://github.com/anne-marziale/ITSjavaPersonne-anne.git
                echo "Repository cloned" 
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                cd ITSjavaPersonne-anne
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                mvn clean
                mvn validate
                mvn compile
                mvn test
                mvn package
                mvn verify
                echo 'Project build' #
                '''
            }
        }

        stage('Run') {
            steps {
                sh '''
                java -jar target/itsjavapersonne-0.1.jar
                echo 'Project run'
                '''
            }
        }
    }
}

