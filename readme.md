# Kustomize POC
This repo provides a good starting point for using Kustomize and an overview of basic usage but does not cover more advanced usage.

### Why Kustomize?
Kustomize has been a native `kind` in k8s since 2017. It will work in k8s and any PaaS option which uses k8s for container orchestration without constraining you to a specific platform.

## Getting started
- [Install Kustomize CLI](https://kubectl.docs.kubernetes.io/installation/kustomize/). That's it!

## Usage walkthrough
### Base folder 
This folder contains the base yaml which will be overwritten based on environment and Kustomize yaml.

### Overlays
This folder contains a directory per environment which will be used to overwrite the base yaml.

### Defining secrets without committing them to git
Kustomize has an inline option to define secrets:

`kustomize edit add secret sl-demo-app --from-literal=db-password=12345`

Note: You can also use a secret from a properties file with `--from-file=file/path` or from env file with `--from-env-file=env/path.env`

### Change image inline
Like for secret, there is a custom directive to allow changing of image or tag directly from the command line. This is very useful if you need to deploy the image previously tagged by your continuous build system.

`kustomize edit set image foo/bar=foo/bar:$TAG_VERSION`

references:
- https://blog.stack-labs.com/code/kustomize-101/
- https://gitlab.com/davinkevin/kustomize-blog-demo