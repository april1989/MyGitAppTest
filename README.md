# An example to explain how to setup your Github repo

The example yaml file is d4config.yml, which has the folloing format: 

```
name: MyGitHubAppExample // the name should be the same as your Github repo
branches: [ master ]     // which branch(es) you want to test
build:
    runs_on: java1.8     // the Java version of your project
    steps:

      - name: Run        // how to build your project (e.g., add a build script for your project),
        run: |
          mkdir bin
          javac -source 1.8 -target 1.8 src/benchmarks/testcases/TestRace6.java -d bin
          
d4tasks: 

  - name: Do_Main        // the task name for each main entry to be analyzed
    which_main_class: benchmarks/testcases/TestRace6     // which main class to analyze for your repo 
    jar: /xx.jar         // where to find your built jars (if any)
    classes: /bin        // where to find your built classes
    exclusions:          // what packages to exclude from the analysis, this can be empty
      java/applet/.*,
      java/awt/.*,
      java/beans/.*,
      java/io/.*,
      java/math/.*,
      java/net/.*,
      java/nio/.*,
      java/rmi/.*,
      java/security/.*,
      java/sql/.*,
      java/text/.*,
      java/util/.*    
      
 - name: Do_Another_Main // another task name for another main entry to be analyzed
    which_main_class: xxx
    ...
```
