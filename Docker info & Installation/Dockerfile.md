A Dockerfile contains a set of instructions to build a Docker image. It defines the base image, application source code, dependencies, and any necessary configuration or commands.

Dockerfile Basics

Understanding Dockerfile Syntax

Dockerfile uses simple instruction statements, each performing a specific action during the image build process.

Common Dockerfile Instructions

Instruction

Description

FROM

Specifies the base image to use

COPY

Copies files from local filesystem into the image

ADD

Similar to COPY, but can also fetch from URLs and unpack archives

RUN

Runs commands inside the image (e.g., installing dependencies)

CMD

Defines the command to run when container starts

ENTRYPOINT

Similar to CMD, but often used for executables

ENV

Sets environment variables

WORKDIR

Sets the working directory inside the image

EXPOSE

Informs which ports the container will listen on

VOLUME

Defines mount points for persistent storage

Best Practices for Writing Dockerfiles

Use a small and efficient base image (e.g., alpine when possible)

Minimize layers by combining commands where feasible

Clean up temporary files in the same layer to reduce image size

Use .dockerignore to avoid unnecessary files being copied

Set explicit versions for dependencies to ensure reproducibility

Example Dockerfile

# Use official Node.js image
FROM node:18

# Set working directory
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy application source
COPY . .

# Expose application port
EXPOSE 3000

# Start application
CMD ["node", "app.js"]

Docker Image

Introduction

A Docker image is the blueprint for a container. It contains:

Application source code

All required dependencies

Configuration

Pre-built Images

Images can be built manually using a Dockerfile.

Pre-built images can also be pulled from Docker Hub or other registries.

Image Caching

Docker caches image layers to speed up builds.

If application code changes, a new image build will update only the changed layers, reusing cache where possible.

