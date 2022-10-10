
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
        stage("Deploy"){
            steps{
                echo ".............Deploy.....nm nbm......"
            }
        }

    }
    
}