#!/usr/bin/groovy
node{
  ws{
    checkout scm
    sh "git remote set-url origin git@github.com:fabric8io/fabric8-maven-plugin.git"

    def pipeline = load 'release.groovy'

    stage 'Stage'
    def stagedProject = pipeline.stage()

    // stage 'Approve'
    // pipeline.approveRelease(stagedProject)

    stage 'Promote'
    pipeline.release(stagedProject)

    stage 'Update downstream dependencies'
    pipeline.updateDownstreamDependencies(stagedProject)
  }
}
