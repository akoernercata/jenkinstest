Jenkinsfile (Declarative Pipeline)
pipeline {
    agent { docker { image 'golang:1.17.5-alpine' } }
     environment {
        PROJECT_ID = 'catalant-test-env'
        CLUSTER_NAME = 'jenkins'
        LOCATION = 'us-west1-c'
        CREDENTIALS_ID = 'jenkins-gke-deployer@.iam.gserviceaccount.com'
    }
    stages {
        stage('Deploy to GKE') {
            steps{
                step([
                $class: 'KubernetesEngineBuilder',
                projectId: env.PROJECT_ID,
                clusterName: env.CLUSTER_NAME,
                location: env.LOCATION,
                manifestPattern: 'manifest.yaml',
                credentialsId: env.CREDENTIALS_ID,
                verifyDeployments: true])
            }
        }
    }
}

