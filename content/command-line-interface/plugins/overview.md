---
title: Overview
weight: 1
---

The command-line interface can be extended using plugins that can be downloaded from either GitHub or private Git Repositories.
Each plugin has to contain a `manifest.yml` file which specifies the feature that are enabled by the plugin.

```Yaml
---
id: 218d3caf07424b10a145ee5e1f036174
name: bitbucket
operations:
    configure:
        enabled: true
        flags:
            - name: user
              shorthand: u
              type: string
              usage: username
            - name: pass
              shorthand: p
              type: string
              usage: password
    environments:
        enabled: true
    pipelines:
        enabled: true
```
