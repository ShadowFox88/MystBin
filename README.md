# MystBin

Easily share code and text.

[Website](https://mystb.in)

[API Documentation](https://mystb.in/api/documentation)

[Install on VSCode](https://marketplace.visualstudio.com/items?itemName=PythonistaGuild.mystbin)


### Running without Docker
**Requirements:**
- Postgres

**Setup:**
- Clone
- Copy `config.template.toml` into `config.toml`
 - Set Database connection DSN.
 - Optionally set URLs to a running Redis Instance.
- ! If you haven't already: Create a Database in `postgres` (Default `mystbin`)
- Install dependencies (Preferably to a `venv`): `pip install -Ur requirements.txt`
- Optionally in `core/server.py` set `ignore_localhost=` to `False` in the RateLimit Middleware for testing.
- Run: `python launcher.py`

### Running with Docker
**Requirements**
- Docker
- Docker Compose

**Setup:**
- Clone
- Copy `config.template.toml` into `config.toml`
  - The default config for database (and redis) should work Out of Box.
  - Ensure you change the `host` key to `0.0.0.0` from `localhost`
- Copy `.env.example` into `.env`
  - The default config should work Out of Box
  - The database container doesn't expose connections outside of the network, but for added security edit `.env` and change the password.
- Optionally in `core/server.py` set `ignore_localhost=` to `False` in the RateLimit Middleware for testing.
- Run `docker compose up -d` to start the services.
  - If you want to use redis for session/limit handling, run with the redis profile: `docker compose --profile redis up -d`
  - The redis container doesn't expose connections outside of the network, but for added security edit `redis.conf` and change the password.
