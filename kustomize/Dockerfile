FROM gcr.io/cloud-builders/gcloud

ENV VER 3.4.0
ENV VERSION v${VER}

COPY kustomize.bash /builder/kustomize.bash

RUN apt-get update && \
    apt-get install -y wget ca-certificates curl wget build-essential && \
    wget https://github.com/kubernetes-sigs/kustomize/releases/download/kustomize%2F${VERSION}/kustomize_${VERSION}_linux_amd64.tar.gz && \
    tar xvzf kustomize_${VERSION}_linux_amd64.tar.gz && \
    mkdir /builder/kustomize && \
    mv kustomize /builder/kustomize/kustomize && \
    chmod +x /builder/kustomize/kustomize && \
    chmod +x /builder/kustomize.bash && \
    rm kustomize_${VERSION}_linux_amd64.tar.gz && \
    apt-get remove --purge -y wget && \
    apt-get --purge -y autoremove && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ENV PATH=/builder/kustomize:$PATH

ENTRYPOINT ["/builder/kustomize.bash"]
