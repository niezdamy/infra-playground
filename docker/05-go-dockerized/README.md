# docker-gs-ping

A simple Go server/microservice example for [Docker's Go Language Guide](https://docs.docker.com/language/golang/). Sample based on repo: (docker-gs-ping)[https://github.com/olliefr/docker-gs-ping]

Notable features:

- Includes a [multi-stage `Dockerfile`](https://github.com/olliefr/docker-gs-ping/blob/main/Dockerfile.multistage), which actually is a good example of how to build Go binaries _for production releases_.
- Has functional tests for application's business requirements with proper isolation between tests using [`ory/dockertest`](https://github.com/ory/dockertest).
- Has a CI pipeline using GitHub Actions to run functional tests in independent containers.
- Has a CD pipeline using GitHub Actions to publish to Docker Hub.

## License

[Apache-2.0 License](LICENSE)
