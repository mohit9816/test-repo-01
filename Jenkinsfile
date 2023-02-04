properties([
                         parameters([
                                  string(name: 'region', defaultValue: 'us-east-1', description: 'Add aws region'),
                                       string(name: 'subnets_list', defaultValue: '"subnet-07d9e4999713e4084,subnet-0556d325e93925333"', description: 'Add n numbers of subnet'),
                                      string(name: 'kms_key_id', defaultValue: 'bc805946-b85e-4073-a896-d7190982348e', description: 'Add kms key'),
                                       [$class: 'ChoiceParameter',
                                            choiceType: 'PT_SINGLE_SELECT',
                                            description: 'Select the RDS DB engine',
                                            filterLength: 1,
                                            filterable: false,
                                            name: 'db_engine',
                                            script: [
                                            $class: 'GroovyScript',
                                            fallbackScript: [
                                            classpath: [],
                                            sandbox: true,
                                            script:
                                            "return['Could not get The DB engine']"
                                            ],
                                            script: [
                                            classpath: [],
                                            sandbox: true,
                                            script:
                                            "return['sqlserver-se','sqlserver-ee','sqlserver-web','sqlserver-ex']"
                                            ]
                                            ]
                                            ],
                                            [$class: 'CascadeChoiceParameter',
                                            choiceType: 'PT_SINGLE_SELECT',
                                            description: 'Select the RDS Option group engine',
                                            name: 'engine_name',
                                            referencedParameters: 'db_engine',
                                            script:
                                            [$class: 'GroovyScript',
                                            fallbackScript: [
                                            classpath: [],
                                            sandbox: false,
                                            script: "return['Could not get engine_name']"
                                            ],
                                            script: [
                                            classpath: [],
                                            sandbox: true,
                                            script: '''
                                            if (db_engine.equals("sqlserver-se")){
                                            return["sqlserver-se"]
                                            }
                                            else if(db_engine.equals("sqlserver-ee")){
                                            return["sqlserver-ee"]
                                            }
                                            else if(db_engine.equals("sqlserver-web")){
                                            return["sqlserver-web"]
                                            }
                                            else if(db_engine.equals("sqlserver-ex")){
                                            return["sqlserver-ex"]
                                            }
                                            '''
                                            ]
                                            ]
                                            ],
                                            [$class: 'CascadeChoiceParameter',
                                            choiceType: 'PT_SINGLE_SELECT',
                                            description: 'Select the RDS Parameter group engine',
                                            name: 'para_engine',
                                            referencedParameters: 'db_engine',
                                            script:
                                            [$class: 'GroovyScript',
                                            fallbackScript: [
                                            classpath: [],
                                            sandbox: true,
                                            script: "return['Could not get para_engine']"
                                            ],
                                            script: [
                                            classpath: [],
                                            sandbox: true,
                                            script: '''
                                            if (db_engine.equals("sqlserver-se")){
                                            return["sqlserver-se-15.0","sqlserver-se-14.0","sqlserver-se-13.0","sqlserver-se-12.0"]
                                            }
                                            else if(db_engine.equals("sqlserver-ee")){
                                            return["sqlserver-ee-15.0","sqlserver-ee-14.0","sqlserver-ee-13.0","sqlserver-ee-12.0"]
                                            }
                                            else if(db_engine.equals("sqlserver-web")){
                                            return["sqlserver-web-15.0","sqlserver-web-14.0","sqlserver-web-13.0","sqlserver-web-12.0"]
                                            }
                                            else if(db_engine.equals("sqlserver-ex")){
                                            return["sqlserver-ex-15.0","sqlserver-ex-14.0","sqlserver-ex-13.0","sqlserver-ex-12.0"]
                                            }
                                            '''
                                            ]
                                            ]
                                            ]
  ])
                        ])
pipeline {
    agent any
    stages {
	    stage ('printing parameters'){
	    steps {
		       script{
			       echo para_engine
			       echo db_engine
			       echo engine_name
		       }
	    }
	    }
	   
   }
}
white_check_mark
eyes
raised_hands
