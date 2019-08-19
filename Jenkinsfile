pipeline{
  agent any
  parameters{
    string(
      name: 'REPOSITORY_PATH',
      defaultValue: 'https://github.com/tavisca-rkaruppaiah/WebApi.git')
    string(
      name: 'SOLUTION_PATH',
      defaultValue: 'WebApi.sln')
    string(
      name: 'TEST_FILE_PATH',
      defaultValue: 'XUnitTestForApi/XUnitTestForApi.csproj')
  }
  stages{
    stage('Build Project'){
      steps{
        powershell '''dotnet restore ${SOLUTION_FILE_PATH} --source https://api.nuget.org/v3/index.json
        
              dotnet${NETCORE_VERSION} build ${SOLUTION_PATH_FILE} -p:CONFIGURATION=release -V:n'''
      }
    }
    stage('Testing Project'){
      steps{
        powershell 'dotnet test ${TEST_PROJECT_PATH}'
      }
    }
    stage('Publishing Project'){
      steps{
        powershell 'dotnet publish XUnitTestForApi/XUnitTestForApi.csproj'
      }
    }
  }
}
