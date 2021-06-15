# From Scratch

## Background

Your organization has been using Kubernetes to manage their deployments for a few months. Already, the size of the YAML pile is growing rapidly.

You're kicking the tires on a couple of ways to address your team's need to get on top of managing these files.

## Current State

For today, you're focusing on just one of the files to determine whether using `ytt` is even going to make sense.

In this example, we take a plain YAML file (a Kubernetes Deployment configuration) and turn it into a `ytt` template.

Along the way, we wish to externalize a few values.

## Your Mission

Convert `config/deployment.yml` into a `ytt` template.

Externalize these values (declaring the Data Values in schema):

- `replicas` to be of type `int`
- `ports` -- a list of port assignments. 
  - each assignment has two keys: `name` (`string`), and `port` (`int`, default: 80)
