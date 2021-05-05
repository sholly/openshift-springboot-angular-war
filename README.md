docker build:

`docker build -f Dockerfile.local -t openshift-war-angular .`

new-app on openshift: 

```shell
oc new-app --as-deployment-config java~https://github.com/sholly/openshift-springboot-angular-war.git \
   --env JAVA_APP_JAR="openshift-springboot-angular-war.war" \
   --build-env ARTIFACT_COPY_ARGS="*.war" \
   --build-env JAVA_APP_DIR="/deployments"
```


Non-deprecated: 


```shell
oc new-app --as-deployment-config java~https://github.com/sholly/openshift-springboot-angular-war.git \
   --env JAVA_APP_JAR="openshift-springboot-angular-war.war" \
   --build-env S2I_SOURCE_DEPLOYMENTS_FILTER="*.war" \
   --build-env JAVA_APP_DIR="/deployments"
```