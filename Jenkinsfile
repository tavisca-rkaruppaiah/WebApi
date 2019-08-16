pipeline {
    agent any
    stages { 
        stage('Restore') {
        	
        	steps{
        		echo 'Restore Step'
        		bat 'dotnet restore WebApi.sln'
        	}
        }
        stage('Build') {
        	
        	steps{
        		echo 'Build step'
        		bat 'dotnet build WebApi.sln -p:Configuration=release -v:q'
        	}
        }
        stage('Test') {
        	
        	steps{
        		echo 'Test step'
        		bat 'dotnet test XUnitTestForAPI/XUnitTestForAPI.csproj'
        	}
        }
        stage('Publish') {
        	
        	steps{
        		echo 'Publish step'
        		bat 'dotnet publish WebApi.sln'
        	}
        }
        stage('Deploy') {
        	
        	steps{
        		echo 'Deploy project'
        		bat 'dotnet WebApi/bin/Release/netcoreapp2.1/WebApi.dll'
        	}
        }
        

    }
   
}

