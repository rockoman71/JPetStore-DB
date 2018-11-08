node { 
    def gitRepo = "https://github.com/rockoman71/JPetStore-DB.git"

    stage('Get source') {
		   git gitRepo
	  }
      
  stage('UrbanCode create version') {
   // class: Defines the Pipeline plug-in to define. The UCD Jenkins Pipeline plug-in’s class name is UCDeployPublisher
   step([$class: 'UCDeployPublisher',
        siteName: 'Default',
	component: [
            $class: 'com.urbancode.jenkins.plugins.ucdeploy.VersionHelper$VersionBlock',
           componentName: 'JPetStore-DB',
           delivery: [
                $class: 'com.urbancode.jenkins.plugins.ucdeploy.DeliveryHelper$Push',
                pushVersion: '${BUILD_NUMBER}',
		baseDir: '/var/lib/jenkins/workspace/JPetStore-DB/',
                fileIncludePatterns: '*',
                fileExcludePatterns: '',              
		incrementalVersion: true,
                pushDescription: 'Pushed from Jenkins'
	    ]	
	]	
    ])
  }
	
stage('UrbanCode Deploy to Dev') {	
   step([$class: 'UCDeployPublisher',
        siteName: 'Default',
        deploy: [
                $class: 'com.urbancode.jenkins.plugins.ucdeploy.DeployHelper$DeployBlock',
                deployApp: 'JPetStore',
                deployEnv: 'DEV-1',
                deployProc: 'Deploy JPetStore',            
                deployVersions: 'JPetStore-DB:${BUILD_NUMBER}',		
                deployOnlyChanged: true
        ]		
    ])
  }
}
