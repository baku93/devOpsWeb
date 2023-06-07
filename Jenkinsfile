pipeline{
    agent any
    tools
    maven 'maven'

    stages{
        stage {Build} {
            steps {
                sh 'mv clean package'
            }
            post{
                success{
                    echo 'Archiving the Artifact'
                    archiveArtifacts artifact: '**/target/*.war'
                }
            }
        }
        stage{'Deploy to tomcat server'} {
            deploy adapters: [tomcat9(path: '', url: 'http://localhost:8081/manager/html')], contextPath: null, war: '**/*.war'
        }
    }
}