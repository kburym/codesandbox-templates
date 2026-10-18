# TDK CLI template

Make a multi-service app with the [TDK CLI](https://github.com/tdk-landscape/tdk-cli-core). You write each service's `service.json`; TDK generates the Dockerfile, routing, and Tiltfile for it. No `docker-compose.yml` or `nginx.conf` to hand-write.

## Make the app

```bash
mkdir shop && cd shop
tdk project --yes
tdk resource orders-api --type backend --stack shop --yes
```

`tdk project` creates the stack. `tdk resource` scaffolds a backend service named `orders-api`, served at `/api/orders`.

## Check the stack

Preview what will start before any container runs:

```bash
npm run tdk:dry-run
```

## Start the stack

`tdk up` needs Docker and Tilt on the machine. Run it on your own machine, or in a container that provides Docker:

```bash
npm run tdk:up
curl http://api.shop.localhost/api/orders/health
```

`tdk up` prints the host ports it chose, so use the URL it prints.

## Learn more

- [Quickstart](https://tdk-landscape.github.io/tdk-website/docs/quickstart/)
- [Examples](https://tdk-landscape.github.io/tdk-website/docs/examples/)
- [What TDK writes](https://github.com/tdk-landscape/tdk-cli-core/blob/main/docs/generated-files.md)
