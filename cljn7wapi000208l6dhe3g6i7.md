---
title: "Jenkins pipelines declarative commands"
datePublished: Mon Jul 03 2023 18:51:36 GMT+0000 (Coordinated Universal Time)
cuid: cljn7wapi000208l6dhe3g6i7
slug: jenkins-pipelines-declarative-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688410231097/fde1b4b7-f84a-4b33-9cf8-6e81ea2e26fc.jpeg
tags: devops, jenkins, devops-articles, 90daysofdevops, trainwithshubham

---

![Jenkins Pipeline – QAutomation](https://q-automations.com/wp-content/uploads/2019/05/pipline.png align="left")

**Pipeline: This command defines the entire Jenkins Pipeline and is the starting point for Declarative Pipeline syntax.**

1. agent: Specifies where the Pipeline will run, defining the execution environment. For example:
    
    ```plaintext
    arduinoCopy codeagent any // Runs the Pipeline on any available agent
    agent { label 'my-label' } // Runs the Pipeline on an agent with a specific label
    ```
    
2. stages: This command groups a series of stages together. A stage represents a logical division within the Pipeline. For example:
    
    ```plaintext
    javascriptCopy codestages {
        stage('Build') {
            // Actions to be performed in the Build stage
        }
        stage('Test') {
            // Actions to be performed in the Test stage
        }
        // More stages can be defined here
    }
    ```
    
3. stage: Defines an individual stage within the stages block. Each stage can have multiple steps or actions. For example:
    
    ```plaintext
    javascriptCopy codestage('Build') {
        steps {
            // Actions to be performed in the Build stage
        }
    }
    ```
    
4. steps: Contains a sequence of one or more steps to be executed within a stage. Each step performs a specific task. Some commonly used steps include:
    
    * sh: Executes a shell command.
        
    * git: Performs Git operations, such as cloning a repository or checking out a specific branch.
        
    * script: Runs a block of scripted Pipeline code.
        
    * echo: Prints a message to the Jenkins console log.
        
5. post: Defines post-build actions that run after all stages have completed. Commonly used post actions include:
    
    *Advance levels:*
    
    1. parameters: Defines input parameters for a Pipeline job. This allows users to provide values during job execution. For example:
        
        ```plaintext
        lessCopy codeparameters {
            string(name: 'PARAM1', defaultValue: 'default', description: 'Parameter 1')
            choice(name: 'PARAM2', choices: ['Option A', 'Option B'], description: 'Parameter 2')
        }
        ```
        
    2. environment: Sets environment variables that are available during the execution of a Pipeline. For example:
        
        ```plaintext
        arduinoCopy codeenvironment {
            FOO = 'bar'
        }
        ```
        
    3. when: Allows conditional execution of a stage or step based on a specific condition. For example:
        
        ```plaintext
        javascriptCopy codestage('Build') {
            when {
                branch 'master'
            }
            steps {
                // Actions to be performed in the Build stage, only for the 'master' branch
            }
        }
        ```
        
    4. tools: Defines specific tools or installations required for the Pipeline job. This allows you to specify tools such as JDK, Maven, or any other custom tool. For example:
        
        ```plaintext
        arduinoCopy codetools {
            maven 'Maven-3.8.1' // Use a specific Maven installation
            jdk 'Java-11' // Use a specific JDK installation
        }
        ```
        
    5. input: Prompts the user to provide input during the execution of a Pipeline. This is useful for manual approvals or interactive steps. For example:
        
        ```plaintext
        lessCopy codeinput(message: 'Proceed with deployment?', ok: 'Deploy')
        ```
        
    6. triggers: Allows defining additional triggers for Pipeline job execution. Commonly used triggers include:
        
        * cron: Schedules the Pipeline to run periodically using cron syntax.
            
        * upstream: Triggers the Pipeline when a specific upstream job completes successfully.
            
        * milestone: Triggers the Pipeline when a specific milestone is reached.
            
    7. options: Specifies additional options and behaviors for the Pipeline. Some commonly used options include:
        
        * skipDefaultCheckout: Skips the default SCM checkout step.
            
        * disableConcurrentBuilds: Ensures that only one instance of the Pipeline job runs at a time.
            
        * timestamps: Adds timestamps to the console log.