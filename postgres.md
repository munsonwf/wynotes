# Postgres

Using psql

## Using `psql`

Install psql on Ubuntu

#### Postgres connection string

`postgres://USERNAME:PASSWORD@DATABASE_URL:5432/DATABSE_NAME`

`postgres://postgres@some-database.us-east-1.amazonaws.com:5432/secret_database`

Unsecure method

You can alternately pass in the password using `USERNAME:PASSWORD` but this is considered unsecure. The password should be omtted from the connection sting, which will then prompt the user to enter it.
