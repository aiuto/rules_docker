# Ubuntu with bazel, gcloud and its dependencies preinstalled.

FROM launcher.gcr.io/google/bazel:latest

# Install gcloud and kubectl
RUN wget https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-220.0.0-linux-x86_64.tar.gz \
    && tar -xzf google-cloud-sdk-220.0.0-linux-x86_64.tar.gz \
    # Add the gcloud binaries to PATH
    && echo 'source /google-cloud-sdk/path.bash.inc' >> ~/.bashrc \
    && ./google-cloud-sdk/install.sh -q \
    # Install kubernetes as a component of gcloud
    && ./google-cloud-sdk/bin/gcloud components install --quiet kubectl

ENV PATH /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/google-cloud-sdk/bin

# Install python tools
RUN apt-get update && apt-get install -y --no-install-recommends \
    python-pip \
    && apt-get clean \
    && python -m pip install --upgrade pip setuptools wheel
