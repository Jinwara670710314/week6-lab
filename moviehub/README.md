# MovieHub

## Run locally

Start PostgreSQL and wait until it is healthy. The first start creates the
`moviehub` database and loads `schema.sql` and `seed.sql` automatically:

```sh
docker compose up -d --wait db
```

Then start the API from this directory:

```sh
export DATABASE_URL="postgres://postgres:secret@127.0.0.1:5432/moviehub"
export JWT_SECRET="$(cat .jwt_secret)"
go run .
```

The API listens on `http://localhost:8080`. To verify it responds, open a
second terminal in this directory and run:

```sh
curl -i http://localhost:8080/api/movies
```

Run the Go tests with:

```sh
go test ./...
```

To stop PostgreSQL without deleting its data:

```sh
docker compose down
```

The Compose credentials are for local development only. The initialization
SQL files run only when PostgreSQL creates a new data volume.
