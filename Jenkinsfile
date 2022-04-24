pipeline {
      agent any
      stages {
          stage('18061692- Stage 1') {
          steps {
            echo 'Begin of Pipeline: Stage one completes'
          }
          }
          stage('18061692-Stage 2') {
          steps {
            input('Do you want to update to Development container?')
          }
          }
          stage('18061692- Stage 3') {
          when {
                not {
                    branch "Development NOT updated"
                }
          }
          steps {
                 sh '''#!/bin/bash
                 targets=websvr_18061692;
                 locate_script='/script_dir/18061692/operate_18061692/script_to_run';
                 docker cp $locate_script $targets://$locate_script;
                 bolt script run $locate_script -t $targets -u clientadm -p user123 --no-host-key-check --run-as root;
                 '''
                 echo "Development container updated"
          }
          }
          stage('18061692- Stage 4') {
          steps {
            echo('Production website tested working.')
                
          }
          }
          stage('18061692- Stage 5') {
          when {
                not {
                    branch "Production NOT updated"
                }
          }
          steps {
                 sh '''#!/bin/bash
                 targets=websvr_18061692;
                 locate_script='/script_dir/18061692/operate_18061692/script_to_run';
                 docker cp $locate_script $targets://$locate_script;
                 bolt script run $locate_script -t $targets -u clientadm -p user123 --no-host-key-check --run-as root;
                 '''
                 echo "Production container updated"
          }
          }
          stage('Completed updating Operation') {
          steps {
            echo 'Production website updated succesfully'
          }
          }
      }
}
