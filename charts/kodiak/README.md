Kodiak Helm chart
=================

> Self-hosted [Kodiak](https://github.com/chdsbd/kodiak), a bot to
automatically update and merge GitHub PRs

## Getting started

Create a Github application, follow the instructions described on the [Kodiak
self-hosting](https://kodiakhq.com/docs/self-hosting) section.

Generate a random secret for the webhook and use it for the `secretKey` value
and add it to the Github App webhook secret, for example:

```bash
$ openssl rand -base64 32
3evN+wAL8sesswc39YtlmaWtlgTitzZ43b7dxs4UP14=
```

Define the `githubAppID`, `githubAppName` and `githubPrivateKey` from the newly
created Github app.

The Github app should be the slug visible in the url, for example:
`https://github.com/organizations/MyOrganisation/settings/apps/kodiak-myorganisation`.
_kodiak-myorganisation_ should be used as application name.

Setup the ingress section in your `values.yaml` file. A publicly accessible
endpoint is required in order to have the webhook working.

For additional settings, look at the `values.yaml` file located in the root of
this Github repository.

Then you are ready to deploy:

```bash
$ helm install --name kodiak --f my-values.yaml kodiak
```

Note: you can use an external Redis instance by setting `redisUrl` and
`redis.enabled: false`, Kodiak require Redis version 5 or higher.
