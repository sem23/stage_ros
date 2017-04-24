pipeline {
  agent {
    node {
      label 'BuildSlave'
    }
    
  }
  stages {
    stage('Checkout') {
      steps {
        dir(path: 'catkin_ws/src') {
          git(url: 'git@github.com:sem23/stage_ros.git', branch: 'master', credentialsId: 'e323d620-0db8-4637-8a6a-3297b65e1c9b', poll: true, changelog: true)
        }
        
      }
    }
    stage('Build') {
      steps {
        sh '''source /opt/ros/indigo/setup.bash
catkin_make'''
      }
    }
    stage('Test') {
      steps {
        sh '''source /opt/ros/indigo/setup.bash
catkin_make run_tests'''
      }
    }
  }
}