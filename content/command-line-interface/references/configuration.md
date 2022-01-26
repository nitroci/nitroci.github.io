---
title: Configuration
weight: 2
---

There are several configurations that can be applied to override default behaviours and values of the command-line interface.

In the event of a conflict then the environment variable configuration ovverrides the Global Config.


{{< toc >}}

## Global Config

A global configuration file is used to configure the cli at operating system level.

{{< tabs "site-config" >}}
{{< tab "TOML" >}}

```Toml
[nitroci]
# Global cache path
cacheHome = "$HOME/.nitro/cache"
```

{{< /tab >}}
{{< tab "YAML" >}}

```Yaml
---
nitroci:
    # Global cache path
    cacheHome: "$HOME/.nitro/cache"
```

{{< /tab >}}
{{< /tabs >}}

## Environment variables

Some of the defaults values can be overriden by the means of the environment variables.

```Shell
# for instance we can override the default global configuration file
export NITROCI_CONFIG="./nitroci/config.ini" && nitroci configure --show
```

Below the comprehensive list of the environment variables:

| VARIABLE NAME        | DEFAULT                 | DESCRIPTION                      |
|----------------------|-------------------------|----------------------------------|
| NITROCI_CONFIG       | $HOME/.nitro/config.ini | Global config path               |
| NITROCI_CACHE   | $HOME/.nitro/cache      | Global cache path                |
