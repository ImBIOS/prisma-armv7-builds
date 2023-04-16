# Prisma precompiled builds for armv7

This repository contains precompiled [prisma-engines](https://github.com/prisma/prisma-engines) for armv7.

## Local Development

### Docker

You can use the provided Dockerfile to build an image to build the engines in the GitHub Actions CI environment. Our target platform was linux/arm/v7, so we need to build the engines in this environment or just use the provided docker image imbios/prisma-armv7-build-image:latest.

```sh
docker build . -t prisma-armv7-build-image --platform linux/arm/v7
docker run -it prisma-armv7-build-image
```

## How to use this repository

This mostly follows this documentation piece, please read this once: <https://www.prisma.io/docs/concepts/components/prisma-engines#using-custom-engine-binaries>

1. Download all 5 Engine files from this repository's GitHub releases page: <https://github.com/ImBIOS/prisma-armv7-builds/releases>
2. Put all the downloaded files into a folder in your project
3. Make sure all 4 binaries are executable using `chmod +x <binary path>`
4. Set the following environment variables in your shell or in the `.env` file:

    ```sh
    PRISMA_QUERY_ENGINE_BINARY=/path/to/query-engine
    PRISMA_MIGRATION_ENGINE_BINARY=/path/to/migration-engine
    PRISMA_INTROSPECTION_ENGINE_BINARY=/path/to/introspection-engine
    PRISMA_FMT_BINARY=/path/to/prisma-fmt
    PRISMA_QUERY_ENGINE_LIBRARY=/path/to/libquery_engine_napi.so.node
    ```

5. You are now ready to use Prisma on your armv7.

## Additional notes

CI in this repository checks for a new major Prisma version everyday and if there is a new release avaliable, it will automatically build the engines and make a new release.
