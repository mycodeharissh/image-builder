FROM innersource-artefacts-docker.optum.cloud/ingested/confluentinc/cp-server-connect:8.1.2
LABEL workstream="Continuous Streaming Service - KAFMRSC (Kafka multi-region stretched cluster)" \
      maintainer="Harish" \
      email="gcpgkekafka@gmail.com" \
      cmdb_appid="AL12345"

USER root
ARG SAR_USER
ARG SAR_PASS

RUN microdnf install -y curl unzip && microdnf clean all

RUN mkdir -p /usr/share/confluent-hub-components/spanner && \
    curl -fsl -u ${SAR_USER}:${SAR_PASS} \
    -o /tmp/spanner.zip \
    "https://artefacts.optum.cloud/repository/innersource-entdp_kafmrsc-maven-release-staging/kafmrsc-connect-spanner-1.2.2.zip" && \
    unzip /tmp/spanner.zip -d /usr/share/confluent-hub-components/spanner && \
    rm -f /tmp/spanner.zip

ENV CONNECT_PLUGIN_PATH = "/usr/share/JAVA,/usr/share/confluent-hub-components"

USER appuser
