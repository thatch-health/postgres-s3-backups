# Deploy a Cron Job to Backup PostgreSQL to Amazon S3

This repo is originally forked from https://github.com/render-examples/postgres-s3-backups.

It is deployed as a cron job on Render in the same environment as the database that needs to be backed up.

The following environment variables must be set:
- `DATABASE_URL`: the _internal_ database URL
- `AWS_REGION`: AWS region where the S3 bucket that will store the backups is located (probably us-west-2)
- `S3_BUCKET_NAME`: name of the S3 bucket where the backups will be stored
- `AWS_ACCESS_KEY_ID` + `AWS_SECRET_ACCESS_KEY`: AWS credentials for a user that has access to the S3 bucket (and ideally nothing else)
- `POSTGRES_VERSION`: Postgres version for the DB being backed up. At the time of this writing, we're running Postgres 15 in all environments, so this would be set to `15`
- `ALPINE_VERSION`: Alpine version. `3.20` for Postgres 15 or 16.
- `DIR_NAME`: top-level directory name where the backups will be stored in S3. Should be the same as the DB instance name on Render, e.g. `thatch-db-staging`.
