FROM scratch

# Docker built-in arg for multi-platform builds
ARG TARGETARCH

STOPSIGNAL SIGINT

# add the default configuration file
COPY config/bulldozer.example.yml /secrets/bulldozer.yml

# add static files
COPY ca-certificates.crt /etc/ssl/certs/

# add application files, selecting the binary for the target architecture
COPY --chmod=0755 bulldozer/build/linux-${TARGETARCH}/bulldozer /bin/bulldozer

ENTRYPOINT ["/bin/bulldozer"]
CMD ["server", "--config", "/secrets/bulldozer.yml"]
