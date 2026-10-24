# Flisk CLI template

Make a multi-service app with the [Flisk CLI](https://github.com/flisk-sh/flisk). You write each service's `service.json`; Flisk generates the Dockerfile, routing, and Tiltfile for it. No `docker-compose.yml` or `nginx.conf` to hand-write.

## Make the app

```bash
mkdir shop && cd shop
flisk project --yes
flisk resource orders-api --type backend --stack shop --yes
```

`flisk project` creates the stack. `flisk resource` scaffolds a backend service named `orders-api`, served at `/api/orders`.

## Check the stack

Preview what will start before any container runs:

```bash
npm run flisk:dry-run
```

## Start the stack

`flisk up` needs Docker and Tilt on the machine. Run it on your own machine, or in a container that provides Docker:

```bash
npm run flisk:up
curl http://api.shop.localhost/api/orders/health
```

`flisk up` prints the host ports it chose, so use the URL it prints.

## Learn more

- [Flisk on GitHub](https://github.com/flisk-sh/flisk)
- [Flisk on npm](https://www.npmjs.com/package/@flisk-sh/flisk)
