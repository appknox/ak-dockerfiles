VERSION 0.8

ak-ubuntu-docker:
    FROM DOCKERFILE -f ak-ubuntu/Dockerfile ak-ubuntu/
    SAVE IMAGE ak-ubuntu:24.04.ak1.0.0

ak-ubuntu-publish:
    FROM DOCKERFILE -f ak-ubuntu/Dockerfile ak-ubuntu/
    FROM +ak-ubuntu-docker
    SAVE IMAGE --push "ghcr.io/appknox/ak-ubuntu":24.04.ak1.0.0

ak-ubuntu-publish-all-platforms:
    BUILD --platform=linux/amd64 --platform=linux/arm64 +ak-ubuntu-publish
