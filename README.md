Manual Deploy Jenkins Instance
-------

1. oc apply -f openshift/buildConfig.yaml

2. oc process openshift/custom-jenkins | oc apply -f -