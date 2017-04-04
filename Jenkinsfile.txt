node {
    stage("Main Build") {
        checkout scm

        docker.image('maven:3.3.9-jdk-8').inside {
            stage("Clean Package") {
                sh 'mvn -B clean package'
            }
        }
    }
}