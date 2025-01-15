# Using Microsoft's Ubuntu-based development container as base image
FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu
COPY upload.sh /usr/local/bin/upload.sh
# Install LaTeX, documentation tools and other utilities
RUN apt-get update && \
apt-get install -y --no-install-recommends nala && \
nala install -y --no-install-recommends curl apt-transport-https ca-certificates && \
curl -sSL https://raw.githubusercontent.com/vegardit/fast-apt-mirror.sh/v1/fast-apt-mirror.sh -o /usr/local/bin/fast-apt-mirror.sh && \
chmod 755 /usr/local/bin/fast-apt-mirror.sh && \
fast-apt-mirror.sh find --apply && \
    # Installing:
    # - texlive packages for LaTeX support with Polish language
    # - chktex for LaTeX syntax checking
    # - biber for bibliography processing
    # - ghostscript for PostScript processing
    # - doxygen and graphviz for documentation generation
    # - python3 for scripting support
    # - inkscape for vector graphics nala update && \
    nala update && \
    DEBIAN_FRONTEND=noninteractive nala install -y texlive-base texlive-latex-extra texlive-lang-polish texlive-luatex chktex texlive-bibtex-extra biber ghostscript doxygen graphviz python3 inkscape && \
    # Removing package cache and unnecessary files to reduce image size
    chmod +x /usr/local/bin/upload.sh && \
    apt-get clean && \
    apt-get autoremove -y && \
    rm -rf \
    /var/lib/apt/lists/* \
    /tmp/* \
    /var/tmp/* \
    /usr/share/doc/* \
    /usr/share/man/* \
    /var/log/* \
    /var/cache/apt/*