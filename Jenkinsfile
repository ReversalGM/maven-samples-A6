pipeline {
  agent any
  tools { 
      maven 'Maven3' 
      jdk 'JDK25' 
  }

  stages {
    stage('check out') {
      steps {
        git(branch: 'master', url: 'https://github.com/dhetong/maven-samples-A6.git')
      }
    }
	
    stage('bisect') {
      steps {
        bat "git bisect start"
        bat "git bisect bad 198644632661c67b6c32f59e9047c11a70685e15"
        bat "git bisect good 98ac319c0cff47b4d39a1a7b61b4e195cfa231e5"
        bat "git bisect run mvn clean test"
        bat "git bisect reset"
      }
    }
  }
}

