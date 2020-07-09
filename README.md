# Kustomization playground

Inside `base` you will find an nginx deployment. Using Kustomize we can make a
series of changes and additions to this base deployment. The `staging` folder
swaps the deployment to use a staging image, as well as scaling the replicas
down. The `prod` folder scales the replicas up and swaps the image to use a
pinned version.


## patchesStrategicMerge
patchesStrategicMerge is a way of patching an existing value inside the base
yml. For example `staging/small-footprint.yml` updates the `replicas` value in
the `base/nginx.yml` to `1`.

## secretGenerator
secretGenerator is a way of generating secrets from inside the
`kustomization.yml`. It handles creating the secrets Resource and encrypting the
values for you. This makes it easy to swap out secrets depending on if you want
to deploy to `staging` or `prod`. You can also references secreets from a file.
See `staging/kustomization.yml` for an example.

## configMapGenerator
configMapGenerator works exactly the same as secretGenerator.
