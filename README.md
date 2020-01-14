Create a Minishift Cluster
-------
Follow the instructions: https://docs.okd.io/latest/minishift/getting-started/preparing-to-install.html

+ Set up your virtualization environment, better use virtual box

+ Install Minishift:
  brew cask install minishift

+ minishift start

Manual Deploy Jenkins Instance on Minishift
-------

1. oc apply -f openshift/buildConfig.yaml

2. oc start-build custom-jenkins-build

3. oc process openshift/custom-jenkins | oc apply -f -