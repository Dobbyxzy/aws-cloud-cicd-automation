FROM jenkins/jenkins:lts

USER root

RUN apt-get update && \
    apt-get install -y docker.io python3 python3-venv && \
    python3 -m venv /opt/awscli && \
    /opt/awscli/bin/pip install --no-cache-dir awscli && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ENV PATH="/opt/awscli/bin:${PATH}"

USER jenkins
