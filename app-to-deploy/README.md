# Deploying an App

## Background

You're about to deploy an application on a Kubernetes cluster.

You've been provided the `ytt`-templated configuration for that application.

Before you _actually_ deploy it, you'd like to render the configuration and be confident it's going to do the right thing.

## Current State

The configuration is found in the `app-to-deploy` directory:

```console
$ cd app-to-deploy
$ tree config
```

This configuration is apparently using the new `ytt` schema features. You've been pointed to the `ytt` documentation: https://carvel.dev/ytt/docs/latest/ytt-schema


## Your Mission

The documentation for this application explains:

> ...
> 
> **Preparing for Deployment**
> 
> Configure the API Server by writing your values file with your custom configuration.
> 
> For example,
> 
> With a file named `values.yml`:
> ```yaml
> #@data/values
> ---
> replica_count: 2
> ```
> running this...
> ```console
> $ ytt -f config/ --data-values-file values.yml
> ```
> 
> will render the customized configuration, setting the number of instances of the API server to 2.
> 
> Refer to the `schema/01-base.yml` for more details.
> 
> ...

Given those instructions, prepare to deploy this controller with your desired configuration:

- controller services three application domains: `dev.example.com`, `stg.example.com`, and `prd.example.com`
- initially deploy 5 instances of the API Server
- Your BLOB store's access key id is "WCYDW37SL4REALLYREAL"

---

_(If there is time, you might attempt this [bonus task](README-bonus.md).)_
