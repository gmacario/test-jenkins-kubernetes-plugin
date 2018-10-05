# Trying again...

Reference: <https://github.com/jenkinsci/kubernetes-plugin/blob/master/README.md#toc25>

```shell
kubectl create namespace kubernetes-plugin

kubectl config set-context \
  $(kubectl config current-context) --namespace=kubernetes-plugin

kubectl create clusterrolebinding cluster-admin-binding \
  --clusterrole=cluster-admin [--user=<user-name>|--group=<group-name>]

kubectl create -f \
  https://raw.githubusercontent.com/jenkinsci/kubernetes-plugin/master/src/main/kubernetes/service-account.yml

kubectl create -f \
  https://github.com/jenkinsci/kubernetes-plugin/raw/master/src/main/kubernetes/jenkins.yml
```

ERROR!

```
gpmacario@nemo:~ $ kubectl create clusterrolebinding cluster-admin-binding   --clusterrole=cluster-admin --user=admin
clusterrolebinding.rbac.authorization.k8s.io/cluster-admin-binding created
gpmacario@nemo:~ $ kubectl create -f \
>   https://raw.githubusercontent.com/jenkinsci/kubernetes-plugin/master/src/main/kubernetes/service-account.yml
serviceaccount/jenkins created
rolebinding.rbac.authorization.k8s.io/jenkins created
Error from server (Forbidden): error when creating "https://raw.githubusercontent.com/jenkinsci/kubernetes-plugin/master/src/main/kubernetes/service-account.yml": roles.rbac.authorization.k8s.io "jenkins" is forbidden: attempt to grant extra privileges: [PolicyRule{APIGroups:[""], Resources:["pods"], Verbs:["create"]} PolicyRule{APIGroups:[""], Resources:["pods"], Verbs:["delete"]} PolicyRule{APIGroups:[""], Resources:["pods"], Verbs:["get"]} PolicyRule{APIGroups:[""], Resources:["pods"], Verbs:["list"]} PolicyRule{APIGroups:[""], Resources:["pods"], Verbs:["patch"]} PolicyRule{APIGroups:[""], Resources:["pods"], Verbs:["update"]} PolicyRule{APIGroups:[""], Resources:["pods"], Verbs:["watch"]} PolicyRule{APIGroups:[""], Resources:["pods/exec"], Verbs:["create"]} PolicyRule{APIGroups:[""], Resources:["pods/exec"], Verbs:["delete"]} PolicyRule{APIGroups:[""], Resources:["pods/exec"], Verbs:["get"]} PolicyRule{APIGroups:[""], Resources:["pods/exec"], Verbs:["list"]} PolicyRule{APIGroups:[""], Resources:["pods/exec"], Verbs:["patch"]} PolicyRule{APIGroups:[""], Resources:["pods/exec"], Verbs:["update"]} PolicyRule{APIGroups:[""], Resources:["pods/exec"], Verbs:["watch"]} PolicyRule{APIGroups:[""], Resources:["pods/log"], Verbs:["get"]} PolicyRule{APIGroups:[""], Resources:["pods/log"], Verbs:["list"]} PolicyRule{APIGroups:[""], Resources:["pods/log"], Verbs:["watch"]} PolicyRule{APIGroups:[""], Resources:["secrets"], Verbs:["get"]}] user=&{gmacario@gmail.com  [system:authenticated] map[user-assertion.cloud.google.com:[AF1jyJC6Lo+EDqXLNK7u34VIVE7GJ1ZlywDsdQP9OJc3GnTCkFq6a/ZaOoJkxM/J6rU4FUgTj/DQtYx09bFg9Hlq0EVnCuQMomTwhWn2BUVC8tI8JlAXEr19bF2220s3mmAFMTdE1etgjX64yFaIy5/TOqJpMb5IUHevYvwLSasSPPNP7EYjSAZ8vfjWpEg3XkJbmK3KEhYYDwPqbfIJlfZmpi0mkeIcSA14uQ==]]} ownerrules=[PolicyRule{APIGroups:["authorization.k8s.io"], Resources:["selfsubjectaccessreviews" "selfsubjectrulesreviews"], Verbs:["create"]} PolicyRule{NonResourceURLs:["/api" "/api/*" "/apis" "/apis/*" "/healthz" "/openapi" "/openapi/*" "/swagger-2.0.0.pb-v1" "/swagger.json" "/swaggerapi" "/swaggerapi/*" "/version" "/version/"], Verbs:["get"]}] ruleResolutionErrors=[]
gpmacario@nemo:~ $
```

<!-- EOF -->
