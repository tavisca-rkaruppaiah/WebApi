pipeline {
    agent any
    stages { 
        stage('Restore') {
        	
        	steps{
        		echo 'Restore Project'
        		sh 'dotnet restore WebApi.sln'
        	}
        }
        stage('Build') {
        	
        	steps{
        		echo 'Build Project'
        		sh 'dotnet build WebApi.sln -p:Configuration=release -v:q'
        	}
        }
        stage('Test') {
        	
        	steps{
        		echo 'Testing Project'
        		sh 'dotnet test XUnitTestForAPI/XUnitTestForAPI.csproj'
        	}
        }
        stage('Publish') {
        	
        	steps{
        		echo 'Publishing Project'
        		sh 'dotnet publish WebApi.sln'
        	}
        }

    }
   
}

