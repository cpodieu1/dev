pipeline {
   agent any
   parameters {
      choice(name: 'VERSION', choices: ['1.1.0','1.2.0', 1.3.0'], description: '')
      booleanParam(name: 'executeTests', defaultValue: true, description: '')
     triggers {
    githubPullRequests spec: '* * * * *', triggerMode: 'HEAVY_HOOKS', events: [labelsAdded(labels('test'))], preStatus: true
  }                                    
   }
   stages {
      stage("build") {
         steps {
             echo 'buildind the application...'
         }
      }
      stage("test") {
         when {
            expression {
                param.executeTests 
            }
         }
         steps {
             echo 'testing the application...'
         }
      }
      stage("deploy") {
         steps {
             echo 'deploying the application'
             echo "deploying version ${params.VERSION}"
            
         }
      }
   }
}                                      

