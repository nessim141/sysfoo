pipeline{

    agent any

// uncomment the following lines by removing /* and */ to enable
    tools{
       maven 'Maven 3.6.3' 
    }
   

    stages{
        stage('Build'){
            steps{
                echo 'Compiling sysfo app'
                sh 'mvn compile'
            }
        }
        stage('test'){
            steps{
                echo 'runnig unit test..'
                sh 'mvn clean test'
            }
        }
        stage('package'){
            steps{
                echo 'packaging the app...'
                sh 'mvn package -DskipTests'
            }
        }
    }
    
    post{
        always{
            echo 'this pipeline has completed...'
        }
        
    }
    
}

