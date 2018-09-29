node {

   stage('Clone repository') { // for display purposes
      // Get some code from a GitHub repository
      git branch: 'develop', url: 'https://github.com/jechavezp/DevopsLearning'
   }

   stage('Prepare files') {
       sh 'chmod +x ./mvnw'
   }

   stage('Run tests and generate tests reports') {
       sh './mvnw surefire-report:report'
   }

   stage('Build arctifact') {
       sh './mvnw package'
   }

   stage('Archive artifacts') {
       archiveArtifacts 'target/*.jar'
   }

    stage('Publish test reports') {
      junit '**/target/surefire-reports/TEST-*.xml'
   }
}