---
title: Configuration
weight: 2
---

There are several configurations that can be applied to override default behaviours and values of the command-line interface.

In the event of a conflict then the environment variables configuration ovverride Global Config.

{{< toc >}}

## Global Config

{{< tabs "site-config" >}}
{{< tab "TOML" >}}

```Toml
[nitroci]
# Path where plugins are stored
pluginPath = "$HOME/.nitro/plugins"
```

{{< /tab >}}
{{< tab "YAML" >}}

```Yaml
---
nitroci:
    # Path where plugins are stored
    pluginPath: "$HOME/.nitro/plugins"
```

{{< /tab >}}
{{< /tabs >}}

## Environment variables

Some of the defaults values can be overriden by the means of the environment variables.

```Shell
# for instance we can override the default global configuration file
export NITROCI_CONFIG="./nitroci/config.ini" && nitroci configure
```

Below the comprehensive list of the environment variables:

| VARIABLE NAME        | DEFAULT                 | DESCRIPTION                      |
|----------------------|-------------------------|----------------------------------|
| NITROCI_CONFIG       | $HOME/.nitro/config.ini | Global config path               |
| NITROCI_PLUGIN_PATH  | $HOME/.nitro/plugins    | Path where plugins are stored    |
