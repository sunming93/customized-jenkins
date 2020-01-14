Manual Deploy Jenkins Instance
-------

1. oc apply -f openshift/buildConfig.yaml

2. oc start-build custom-jenkins-build

3. oc process openshift/custom-jenkins | oc apply -f -