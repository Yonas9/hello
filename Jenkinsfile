pipeline {

  agent any
  environment {
    //adding a comment for the commit test
    DEPLOY_CREDS = credentials('deploy-anypoint-user')
    MULE_VERSION = '4.4.0'
    BG = "SelfTaught"
    WORKER = "Micro"
    M2SETTINGS = "C:\\Users\\Yonas_Eluna\\.m2\\settings.xml"
  }
  stages {
    stage('Build') {
      steps {
      		bat 'mvn clean -DargLine="--add-exports=java.base/sun.net.www.protocol.jar=ALL-UNNAMED"'
      
           
          
            
      }
    }

    
    }

     stage('Deploy Development') {
      environment {
        ENVIRONMENT = 'Sandbox'
        APP_NAME = 'helloWorld2023'
      }
      steps {
            bat 'mvn -U -V -e -B -gs %M2SETTINGS% -DskipTests deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%" -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKER%"'
      }
    }
    stage('Deploy Production') {
      environment {
        ENVIRONMENT = 'Production'
        APP_NAME = 'helloWorld2023'
      }
      steps {
            bat 'mvn -U -V -e -B -gs %M2SETTINGS% -DskipTests deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%" -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKER%"'
      }
    }
  }
