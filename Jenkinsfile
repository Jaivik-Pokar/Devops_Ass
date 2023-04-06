pipeline{
    agent any

    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }

        }
        stage('Depoy to tomcat server'){
            steps{
                depoy adapters: [tomcat7(credentialsID: '58cccd86-7ec3-4a1a-8dfd-8f664aff0392',path:'',url: 'https://3.108.221.41:8282')], contextPath:null, war: '**/*.war'
            }

        }
        
    }
}