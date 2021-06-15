# Authoring a Kubernetes Deployment

## Background

You are a platform engineer... and you've started a new gig.

One of the many things you've inherited is managing a Kubernetes cluster. Your predecessor — in her infinite wisdom — used `ytt` to template out the Kubernetes configuration files.

You've been reading up on this new fandangled "Schema" feature in `ytt` and thought you'd give it a whirl.

## Current State
You read through the existing configuration: `config/secret.yml` and note it does the following:

1. Checks presence of data values (and fails if not provided):
   - jwt
   - jwt.policy
   - jwt.policy.activeKeyId
2. Checks that the type of jwt.policy.keys is a map
3. Provides default value of 20 to uses if not provided explicitly in data values.

If you run this through `ytt` with the sample values you get:

```console
$ ytt -f config/ --data-values-file sample-values.yml
```

it gives:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: uaa-jwt-policy-signing-keys
  annotations:
    uses_remaining: "20"
type: Opaque
stringData:
  jwt_policy_signing_keys.yml: |
    jwt:
      token:
        policy:
          activeKeyId: default_jwt_signing_key
          keys:
            default_jwt_signing_key:
              signingKey: jwt_policy_signing_key
```

## Your Mission

Create a Schema for the data values of this configuration:

1. Add a file `config/schema.yml`
2. In that file, write a schema for the data values `config/secret.yml` expects. The schema should:
    - declares the following Data Values (and fails if not provided):
        - `jwt`
        - `jwt.policy`
        - `jwt.policy.activeKeyId`
    - Checks `jwt.policy.keys` has the right structure (i.e. is a map with specific keys)
    - Provides default value of 20 to `uses` if not provided explicitly in data values.

**NOTE:** Be sure to delete any code that is no longer needed!
