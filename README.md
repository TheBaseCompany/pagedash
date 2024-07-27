# Get started 

0. Prepare an .env file
1. Install packages
```
yarn install
```
2. Start dev
```
yarn dev
```

# Deployment
## Build with secret from .env.production.local
```bash
fly deploy $(grep -v '^#' .env.production.local | awk -F= '{print "--build-arg "$1"="$2}')
```
Output sample:
```bash
fly deploy --build-secret DB_HOST=localhost --build-secret DB_USER=user --build-secret DB_PASS=secret --build-secret API_KEY=key123
```

## Set secret to fly from .env.production.local
```bash
fly secrets set $(grep -v '^#' .env | xargs)
```


