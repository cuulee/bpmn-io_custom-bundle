#!/usr/bin/env groovy

/*
 * Template Jenkinsfile for process-engine projects.
 *
 * For this template to work you need some custom
 * scripts in your package.json. Below is a example
 * for those scripts:
 *  (...)
 *  "scripts": {
 *    "lint": "gulp lint",
 *    "build": "gulp build",
 *    "build-schemas": "gulp typescript-schema"
 *    "build-doc": "gulp doc",
 *    "test": "gulp test",
 *  },
 *  (...)
 *
 */
pipeline {
  agent any
  tools {
    nodejs "node-lts"
  }

  stages {
    stage('prepare') {
      steps {
        sh 'node --version'
        sh 'npm install --ignore-scripts'
      }
    }
    stage('build') {
      steps {
        sh 'node --version'
        sh 'npm run build'
      }
    }
    stage('publish') {
      when {
        branch 'master'
      }
      steps {
        nodejs(configId: 'process-engine-ci-token', nodeJSInstallationName: 'node-lts') {
          sh 'node --version'
          sh 'npm publish --ignore-scripts'
        }
      }
    }
  }
}
