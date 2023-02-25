node {
    def app
    
    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'GitHub-Credentials', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email wiz.obi7509@gmail.com"
                        sh "git config user.name obinnaaliogor"
                        //sh "git switch master"
                        sh "cat springapp.yml"
                        sh "sed -i 's+obinnaaliogor/spring-boot-mongo.*+obinnaaliogor/spring-boot-mongo:${DOCKERTAG}+g' springapp.yml"
                        sh "cat springapp.yml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/spring-boot-docker.git HEAD:master"
      }
    }
  }
}
}
