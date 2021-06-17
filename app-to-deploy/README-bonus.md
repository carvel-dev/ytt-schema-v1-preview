# Deploying an App

_(This is a follow-up to a previous task. If you haven't done the [first task](README.md), yet, stop here and do that before preceding.)_

## Bonus: Enabling Honeycomb

You've been asked to also enable Honeycomb for this deployment.

It's not necessary to understand what Honeycomb is or does. What is important is to know that it's an optional piece of configuration for this deployment.

The relevant section in the documentation includes this:

> ...
> 
> **Configuring Honeycomb**
>
> For debugging, it may be useful to emit events to Honeycomb. This can be enabled by
> passing an additional data values file to the `ytt` command.
>
> `honeycomb-values.yml`
> ```
> ---
> honeycomb:
>   dataet: my-dataset
>   writekey: MY_WRITE_KEY
> ```
>
> ```console
> $ ytt -f config/ --data-values-file values.yml --data-values-file honeycomb-values.yml
> ```
> ...
