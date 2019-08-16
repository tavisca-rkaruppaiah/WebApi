pipeline {
    agent any
    stages { 
        stage('Restore') {
        	
        	steps{
        		echo 'Restore Project'
        		bat 'dotnet restore WebApi.sln'
        	}
        }
        stage('Build') {
        	
        	steps{
        		echo 'Build Project'
        		bat 'dotnet build WebApi.sln -p:Configuration=release -v:q'
        	}
        }
        stage('Test') {
        	
        	steps{
        		echo 'Testing Project'
        		bat 'dotnet test XUnitTestForAPI/XUnitTestForAPI.csproj'
        	}
        }
        stage('Publish') {
        	
        	steps{
        		echo 'Publishing Project'
        		bat 'dotnet publish WebApi.sln'
        	}
        }

    }
   
}

