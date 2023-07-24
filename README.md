# Production grade Metabase deployment with Trino

Note: this is a sample, not something you might want to use as a deployment on a production tenant. Please remember the separation of concerns

## Components
- Nginx acting as a reverse proxy. Listens on port 8443 (public port, SSL) and sends traffic to Metabase on port 3000
- Metabase, listening on port 3000, only to Nginx. This Metabase instance is also custom built, to work on ARM machines as well, but also with the Starburst driver
- Postgres application database: where Metabase will save all its data
- Trino server: listening publicly on port 8444
- MySQL DB and MongoDB: two databases with sample data. Trino will connect to these and you'll see these 2 also in Metabase as separate connections
- Maildev: a simple email server so you can try Metabase subscriptions (listening publicly on port 3003)
- Setup container: a simple script that will initialize Metabase when it's ready

## Credentials
- Metabase: a@b.com / metabot1
- Trino: admin