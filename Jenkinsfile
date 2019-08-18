pipeline
{
  agent any
  parameters
  {
   choice
   (
      choices: ['BUILD' , 'TEST' , 'PUBLISH','CREATE_DOCKER_FILE'],
      name: 'CHOSEN_ACTION'
   )
    string
    (
      name: 'REPOSITORY_PATH',
      defaultValue: 'https://github.com/tavisca-rkaruppaiah/WebApi.git'
    )
    string
    (
      name: 'SOLUTION_PATH',
      defaultValue: 'WebApi.sln'
    )
    string
    (
      name: 'TEST_FILE_PATH',
      defaultValue: 'XUnitTestForApi/XUnitTestForApi.csproj'
    )
  }
  stages
  {
    stage('Build Project')
    {
      when 
      {
        expression 
        {
        	params.CHOSEN_ACTION == 'BUILD' ||  params.CHOSEN_ACTION == 'TEST' ||  params.CHOSEN_ACTION == 'PUBLISH'
        }
      }
      steps
      {
        powershell '''dotnet restore ${SOLUTION_FILE_PATH} --source https://api.nuget.org/v3/index.json
        
              dotnet${NETCORE_VERSION} build ${SOLUTION_PATH_FILE} -p:CONFIGURATION=release -V:n'''
      }
    }
    stage('Testing Project')
    {
      when 
      {
        expression 
        { 
        	params.CHOSEN_ACTION == 'TEST' ||  params.CHOSEN_ACTION == 'PUBLISH'
        }
      }
      steps
      {
        powershell 'dotnet test ${TEST_PROJECT_PATH}'
      }
    }
    stage('Publishing Project')
    {
      when 
      {
        expression 
        {
        	params.CHOSEN_ACTION == 'PUBLISH'
        }
      }
      steps
      {
        powershell 'dotnet publish XUnitTestForApi/XUnitTestForApi.csproj'
      }
    }
    stage('Converting File')
    {
      when 
      {
        expression 
        {
        	params.CHOSEN_ACTION == 'PUBLISH'
        }
      }
      steps
      {
        zip zipFile: 'publish.zip', archive: false, dir: 'WebApi/bin/Debug/netcoreapp2.2/publish'
        archiveArtifacts artifacts: 'publish.zip', fingerprint: true
      }
    }
  }
  post
  {
    always
    {
      deleteDir()
      powershell 'echo Release...'
    }
  }
}
