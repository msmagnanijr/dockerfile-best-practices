### Dockerfile Issues

- Running application as root --> run as non-root user
- Minimize image size --> base image with minimal dependencies
- Using chown when COPY or ADD files --> avoiding permission issues
