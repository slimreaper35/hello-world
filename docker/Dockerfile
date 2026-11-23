# Build context is the repository root (ContextDir "." in the e2e scenario),
# this file lives at docker/Dockerfile to match constants.DockerFilePath.
FROM registry.access.redhat.com/ubi9/python-312:latest

WORKDIR /opt/app-root/src

COPY --chown=1001:0 pyproject.toml README.md ./
COPY --chown=1001:0 src ./src

ENV PYTHONPATH=/opt/app-root/src/src \
    PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

USER 1001

LABEL name="hello-world" \
      vendor="Red Hat, Inc." \
      version="0.1.0" \
      release="1" \
      summary="Dummy Python application for container build e2e tests" \
      description="Dummy Python application used to exercise the container-build-catalog e2e build pipelines." \
      io.k8s.display-name="hello-world" \
      io.k8s.description="Dummy Python application used to exercise the container-build-catalog e2e build pipelines." \
      io.openshift.tags="python,sample,e2e"

CMD ["python", "-c", "from hello_world import main; main()"]
