# syntax=docker/dockerfile:1.4-labs

FROM --platform=${BUILDPLATFORM} mgoltzsche/podman:minimal AS builder

ARG TARGETARCH
ENV TARGETARCH "${TARGETARCH}"

WORKDIR /build

COPY images/manifest.txt images/preload ./
RUN --security=insecure ./preload manifest.txt

FROM rancher/k3s:v1.24.4-k3s1

ARG TARGETARCH

COPY --from=builder /build/images/ /var/lib/rancher/k3s/agent/images/
COPY images/tar/${TARGETARCH}/ /var/lib/rancher/k3s/agent/images/
COPY manifests/ /var/lib/rancher/k3s/server/manifests/
COPY bin/ /bin/

ENTRYPOINT [ "/bin/k3d-entrypoint.sh" ]
CMD [ "server", "--disable=traefik", "--disable=servicelb" ]
