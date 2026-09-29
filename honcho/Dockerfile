# Honcho v3.1.2, pinned to its multi-platform manifest (amd64 and arm64).
# Its default command skips migrations and starts only the API. Cubeship
# has no command override, so the same wrapper selects API or deriver.
FROM ghcr.io/plastic-labs/honcho:v3.2.1@sha256:a6bf2f03d47d91281521830ba2a32710a60bde207c37c8f2049fd1ac7619c6d9
COPY --chown=app:app start.py /app/cubeship-start.py
ENTRYPOINT ["/app/.venv/bin/python", "/app/cubeship-start.py"]
CMD []
