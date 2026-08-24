# Getting Started With Builds on OpenShift

## Intro

There are lots of ways to build your apps on OpenShift, including your favourte open source or 3rd party tooling (e.g. Jenkins, GitLab Runners, etc...).  However, OpenShift offers two main fully supported options "out of the box" - [OpenShift Pipelines](https://docs.redhat.com/en/documentation/red_hat_openshift_pipelines/latest) (Tekton) and [Builds for Red Hat OpenShift](https://docs.redhat.com/en/documentation/builds_for_red_hat_openshift/latest) (Shipwright).

This demo repository will show you how to use each.

## Prerequisites

1. Red Hat OpenShift Container Platform cluster (4.20+)
2. OpenShift Pipelines Operator (latest)
3. Builds for Red Hat OpenShift Operator (latest)
4. Application source code repository to test your builds

### Step 1:  OpenShift Pipelines

Builds for Red Hat OpenShift relies on OpenShift Pipelines, so both of these examples will require this operator to be installed.  Install the **OpenShift Pipelines** Operator from OperatorHub.

### Step 2:  Builds for Red Hat OpenShfit

Once OpenShift Pipelines is installed, install the **Builds for Red Hat OpenShift** Operator in the `openshift-builds` namespace.  If you use the OperatorHub UI, this is the default namespace that will be created for you.  If you are deploying this operator using the CLI, you will need to create this namespace ahead of time.

### Step 3:  Initialize Shipwright

Once the **Builds for Red Hat OpenShift** is installed, you initialize Shipwright by applying the following CR:

```
apiVersion: operator.shipwright.io/v1alpha1
kind: ShipwrightBuild
metadata:
  name: cluster
spec:
  targetNamespace: openshift-builds
```

## OpenShift Builds / Shipwright

* [Demo Java and NodeJS builds with Shipwright](shipwright/README.md)
* [Demo Java and NodeJS builds with Tekton](tekton/README.md)