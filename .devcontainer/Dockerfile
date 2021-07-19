ARG APAMA_VERSION
FROM store/softwareag/apama-builder:${APAMA_VERSION}

USER root
RUN microdnf install git
RUN microdnf install python3

WORKDIR "/usr/local/bin"
COPY apama apama
RUN chmod +x apama

USER sagadmin
WORKDIR "/opt/softwareag"
RUN git clone https://github.com/SoftwareAG/apama-analytics-builder-block-sdk.git

ENV ANALYTICS_BUILDER_SDK=/opt/softwareag/apama-analytics-builder-block-sdk
WORKDIR ${ANALYTICS_BUILDER_SDK}
ARG APAMA_ANALYTICS_BUILDER_SDK_BRANCH
RUN git checkout ${APAMA_ANALYTICS_BUILDER_SDK_BRANCH}
ENV PATH="${ANALYTICS_BUILDER_SDK}:${PATH}"