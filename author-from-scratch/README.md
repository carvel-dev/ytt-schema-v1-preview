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
  - each assignment has two keys: 
    - `name` (`string`) — the name of the container who's port you're specifying, and
    - `port` (`int`, default: 80) — the port on which that container will listen.
  
If someone runs your template through `ytt` with a corresponding data values file,

`values.yml`
```yaml
#@data/values
---
replicas: true
ports:
- name: front-end
  port: "8080"
- name: rss-reader
  port: "8088"
```

```console
$ ytt -f config/ --data-values-file values.yml
```

They will (after fixing a few errors) find their way to:

```yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: rss-site
  labels:
    app: web
spec:
  replicas: 10
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
      - name: front-end
        image: nginx
        ports:
        - containerPort: 8080
      - name: rss-reader
        image: nickchase/rss-php-nginx:v1
        ports:
        - containerPort: 8088
```
