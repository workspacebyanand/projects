
//declarative pipeline]
pipeline{
    agent any

    tools{
         maven "maven"
    }

    
    environment{
        // to read values from pom.xml 
        ArtifactId = readMavenPom().getArtifactId()
        Version = readMavenPom().getVersion()
        Name = readMavenPom().getName()
        GroupId = readMavenPom().getGroupId()

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
                script{

                    def Nexusrepo = Version.endsWith("SNAPSHOT") ? "AnandDevopsLab-SNAPSHOT" : "AnandDevopsLab-RELEASE "
                    // jenkins pipline script using snippet generator

                    nexusArtifactUploader artifacts:
                    [[artifactId: "${ArtifactId}",
                    classifier: '', 
                    file: "target/${ArtifactId}-${Version}.war",
                    type: 'war']], 
                    credentialsId: 'd7040dca-986d-4147-9712-9f19fe20fdb4', 
                    groupId: "${GroupId}", 
                    nexusUrl: '172.20.10.136:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: "${Nexusrepo}", 
                   version: "${Version}"
                }
            }

        }

        // print pom.xml values
        stage("print Environment values"){
            steps{
                echo "ArtifactId is ${ArtifactId}"
                echo "Version is ${Version}"
                echo "Name is ${Name}"
                echo "GroupId is ${GroupId}"
            }

        }


        stage("Deploy"){
            steps{
                echo ".............Deploy.....nm nbm......"
            }
        }

    }
    
}