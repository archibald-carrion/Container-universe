# Dockerfile
FROM alpine:latest

ARG DOCKER_GID=989

# Install bash first, as it's needed for the CMD instruction
RUN apk update && \
    apk add --no-cache bash docker-cli

# Create docker group with proper GID and non-root user
RUN addgroup -g ${DOCKER_GID} docker && \
    addgroup -g 1001 ci && \
    adduser -D -u 1001 -G ci -s /bin/sh ci && \
    adduser ci docker

USER ci
WORKDIR /home/ci
CMD ["bash"]

# alternate Dockerfile for a Docker CLI image

# FROM docker:25.0.3-cli

# ARG DOCKER_GID=989

# # Recreate docker group with correct GID, then set up user
# RUN delgroup docker || true && \
#     addgroup -g ${DOCKER_GID} docker && \
#     addgroup -g 1001 ci && \
#     adduser -D -u 1001 -G ci -s /bin/sh ci && \
#     adduser ci docker

# USER ci
# WORKDIR /home/ci
# CMD ["sh"]
