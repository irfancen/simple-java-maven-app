node {
    withDockerContainer(args: '-v /root/.m2:/root/.m2', image: 'maven:3.9.0') {
        stage('Build') {
            sh 'mvn -B -DskipTests clean package'
        }

        stage('Test') {
            try {
                sh 'mvn test'
            }
            catch(e) {
            
            }
            finally {
                junit 'target/surefire-reports/*.xml'
            }
        }

        stage('Deliver') {
            sh './jenkins/scripts/deliver.sh'
        }
    }
}