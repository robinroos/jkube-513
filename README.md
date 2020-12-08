# jkube-513
Test case based on Spring Hello World for JKube issue 513

This project is intended to reproduce JKube #513.

Spring Boot has been taken up to 2.4.0

openshift-maven-plugin is version 1.0.2

Jkube service type is ClusterIP 

When I run it in my environment it actually reproduces:

OpenShift platform has been specified but OpenShift has not been detected!

However, the generated openshift.yml contains the key feature of issue 513, the definition of the hazelcast port mapping TCP 5701 -> 5701 without the "name" property.

My environment settings and build sequence is:

set KUBECONFIG=C:\users\roosro\.kube\config
set KUBERNETES_TRUST_CERTIFICATES=true
oc login
oc project cacheui
mvn -Popenshift -Prr clean package oc:resource oc:build

Profile "rr" introduces environment specific properties (here redacted).

After running my maven command I archived some of the generated files to:

target_classes_META-INF_jkube
target_classes_META-INF_jkube_openshift

representing what was in target/classes/META-INF/jkube/openshift

