---
title: Nitro CI
geekdocFlatSection: false
---

**Boost your software Development, Continuous Integration and Deployment with Nitro CI.**

{{< hint info >}}
**Nitro CI** aims to create **workspaces** which are **compliant to devops practices** farthermore provide **tools to implement commands** that can be executed in the local development environment as well as in the CI and CD environments without having to maintain multiple stacks. This is not limited to shell commands but it enbales practices to manage environments, encryption, pipelines and much more.
{{< /hint >}}
For instance a developer using K8S locally (K3d, K3s, Kind, MicroK8s, and MiniKube) is able to test the complete CI and CD process on its own local development.

Just to be clear no more README files to document commands and deployment procedures to be executed by either the developer or the release manager.

Workspaces can be composed in a hierarchical way and they are not tied to a single git repository hence a workspace can be composed by multiple git repositories and there is no limit to have just one workspace for each git repository.

This can be quite useful in contexts where the developer has to draft the structure of the project and it is not clear how to split it into one or more git repositories, a pratical use case can be either microservices/serverless developement or refactoring which is aimed to extract common libraries.

A workspace can be used with any type of project and it is not tied to a particolar programming language. This approach plays quite well and shines with Cloud Native, Microservices and Serverless applications as they require complex automation.

The stack can be extended to include your preferred DevOps tools (For instance CI & CD tools and Package Manager as long as they expose any kind of Api for the integration).

<!-- spellchecker-disable -->

<!-- spellchecker-enable -->
