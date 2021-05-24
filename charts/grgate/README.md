GRGate Helm chart
=================

> Git release gate utility which autopublish draft/unpublished releases based
on commit status

## Getting started

Create a Github application/Gitlab Token, follow the instructions described on
the [GRGate installation](https://github.com/FikaWorks/grgate) section.

Generate a random secret for the webhook and use it for the
`config.server.webhookSecret` value and add it to the Gitlab/Github App webhook
secret, for example:

```bash
$ openssl rand -base64 32
3evN+wAL8sesswc39YtlmaWtlgTitzZ43b7dxs4UP14=
```

Setup the ingress section in your `values.yaml` file. A publicly accessible
endpoint is required in order to have the webhook working.

For additional settings, look at the `values.yaml` file located in the root of
this directory.

Then you are ready to deploy:

```bash
$ helm install --name grgate --f my-values.yaml fikaworks/grgate
```

