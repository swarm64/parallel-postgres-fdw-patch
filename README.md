# Patch to make `postgres_fdw` parallel-safe

This patch makes the `postgres_fdw` foreign data wrapper parallel-safe so that shards stored on remote servers can be accessed in parallel via a `Parallel Append` plan node.

**Note, that the patch is experimental.**

To compile and use the patch follow these instructions:

1. Get the PostgreSQL source code, for example via
    - `git clone https://github.com/postgres/postgres.git --depth=1` or
    - `apt-get source postgresql-11` and `sudo apt-get build-dep postgresql-11`
1. Apply the patch from this repository to `contrib/postgres_fdw/postgres_fdw.c`
1. Compile PostgreSQL
1. Copy `postgres_fdw.so` to `$(LIBDIR)`
1. Copy `postgres_fdw.control` to $(SHAREDIR)/extension/
1. Copy `postgres_fdw--1.0.sql` to $(SHAREDIR)/extension/
1. Restart PostgreSQL
