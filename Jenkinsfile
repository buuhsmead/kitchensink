node('maven') {
  stage('Checkout') {
	checkout([$class: 'GitSCM', branches: [[name: 'refs/heads/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'huubatgit', url: 'http://gogs-xyz-gogs.apps.127.0.0.1.nip.io/huub/kitchensink.git']]])

}
  
  stage('Build') {
       // sh "pwd"
       // sh "ls -ltra"
        sh "mvn -Dmaven.test.failure.ignore clean package -s nexus_settings.xml"
    }

stage('Release') {
  sh "git config user.name ocp-jenkins"
  sh "git config user.email you@example.com"
  sh "mvn -Dmaven.test.failure.ignore -s .openshift/nexus_settings.xml -B clean release:prepare release:perform"
}

}
