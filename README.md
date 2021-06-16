# ytt-schema-v1-preview

## Welcome and Thank You!

Greetings.

We're using the information we gather in this session to help us make the Schema feature better.

Thank you for your help!

## Setup

A few steps to take before we get going...

1. Make sure you've installed the latest version of `ytt`: https://github.com/vmware-tanzu/carvel-ytt/releases

2. Either clone or download a copy of this repository to your machine:
   ```console
   git clone https://github.com/k14s/ytt-schema-v1-preview.git
   cd ytt-schema-v1-preview 
   ```
   
3. Let's enable the schema features by default using an alias.
   ```console
   alias ytts='ytt --enable-experiment-schema'  
   ```
   and verify it's working...
   ```console
   ytts -f app-to-deploy/config
   ```

## Housekeeping

- **whatever occurs to you _is_ what we're most interested in** -- you are not being tested.
- **think out loud** -- your words don't have to make sense to anyone but you...

---

With that all set, let's head to our [first task](app-to-deploy/README.md).
