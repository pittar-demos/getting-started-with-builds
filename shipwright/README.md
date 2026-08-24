# OpenShift Builds / Shipwright

**Docs:** [Builds for Red Hat OpenShift](https://docs.redhat.com/en/documentation/builds_for_red_hat_openshift/latest) 

## Build Examples:  Java and NodeJS

OpenShift Builds allows you to use many different strategies and technologies for builds.  This includes `Buildah`, `source-to-image`, and `buildpack`.  The examples below are for a "Cloud Native Build Pack" Java and NodeJS builds.

## Build and Deploy

For simplicity, this will use a single namespace/project and the internal OpenShift image registry.  You can use external registries and private repositiries as well, you simply have to configure the appropriate `Secrets` with credentials and change the `Build` yaml according.

### Deploying the Examples

The examples can be deployed with one CLI command each.  Once the initial builds are completed, the associated `Deployments` need to be scaled up to 1.

#### NodeJS

```
oc apply -k manifests/node
```

This will:
* Create a namespace (`node-build-demo`).
* Create a `Build`
* Kick off the initial `BuildRun`
* Create the associated `Deployment`, `Service`, and `Route`

Once the build completes, you can manually scale the app deployment to 1.  Once it is running, click on the route to see the live app (a simple API that returns `Hello world`).

#### Java / Quarkus

```
oc apply -k manifests/java
```

This will:
* Create a namespace (`node-build-demo`).
* Create a `Build`
* Kick off the initial `BuildRun`
* Create the associated `Deployment`, `Service`, and `Route`

Once the build completes, you can manually scale the app deployment to 1.  Once it is running, click on the route and append `/hello` to see the live app (a simple API that returns `hello`).