node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("bisera-G/pls")
    }
    stage('Push image') {   
        docker.withRegistry('https://registry.hub.docker.com', 'df658a4c-ca20-410f-8b96-a09e40dc3f9b') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
            // signal the orchestrator that there is a new version
        }
    }
}
