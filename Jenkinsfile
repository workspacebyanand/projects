
//declarative pipeline]
pipeline{
    agent any

    tools{
         maven "maven"
    }
    stages{
        stage("Build"){
            steps{
                sh 'mvn clean install'
            }
         
        }
        stage("Test"){
            steps{
                echo "............testing............"
            }
        }

        //publish artifact to nexus
        stage("publish to nexus"){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'demo-project', classifier: '', file: 'target/demo-project-0.0.4-SNAPSHOT.jar', type: 'jar']], credentialsId: 'd7040dca-986d-4147-9712-9f19fe20fdb4', groupId: 'com.cg', nexusUrl: '172.20.10.136:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'AnandDevOpsLab-SNAPSHOT', version: '0.0.4-SNAPSHOT'
            }

        }
        stage("Deploy"){
            steps{
                echo ".............Deploy.....nm nbm......"
            }
        }

    }
    
}