# Sample Function: TypeScript "Hello World"

## Introduction

This repository contains a sample "Hello World" function written in TypeScript. You can deploy it on DigitalOcean's App Platform as a Serverless Function component or as a standalone Function. Documentation is available at https://docs.digitalocean.com/products/functions.

### Requirements

* You need a DigitalOcean account. If you don't already have one, you can sign up at [https://cloud.digitalocean.com/registrations/new](https://cloud.digitalocean.com/registrations/new).
* To deploy from the command line, you will need the [DigitalOcean `doctl` CLI](https://github.com/digitalocean/doctl/releases).

## Deploying the Function

```bash
# clone this repo
git clone git@github.com:digitalocean/sample-functions-typescript-helloworld.git
```

```
# deploy the project, using a remote build so that compiled executable matched runtime environment
> doctl serverless deploy sample-functions-typescript-helloworld --remote-build
Deploying 'sample-functions-typescript-helloworld'
  to namespace 'fn-...'
  on host 'https://faas-...'
Submitted action 'hello' for remote building and deployment in runtime typescript:default (id: ...)

Deployed functions ('doctl sls fn get <funcName> --url' for URL):
  - sample/hello
```

## Using the Function

### `doctl` CLI
```bash
doctl serverless functions invoke sample/hello
```
```json
{
  "body": "Hello stranger!"
}
```

### `doctl` CLI with a request Body
```bash
doctl serverless functions invoke sample/hello -p name:Sammy
```
```json
{
  "body": "Hello Sammy!"
}
```

### `curl`
```bash
curl $(doctl sls fn get sample/hello --url)
```
```
Hello stranger!
```

💡 The output above is not in json format because it's performing an HTTP get directly and the body of the function does not return a json object, but a plain string.

### Learn More

You can learn more about Functions and App Platform integration in [the official App Platform Documentation](https://www.digitalocean.com/docs/app-platform/).
