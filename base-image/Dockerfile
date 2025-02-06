FROM pangeo/pangeo-notebook:2025.01.24

ENV DATA_GID=16301 \
    DATA_GROUP=certainty

USER root

RUN echo "Installing packages..." \
    && apt-get update --fix-missing > /dev/null \
    && apt-get install -y nco cdo > /dev/null \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN echo "Adding user to data group..." \
    && groupadd --gid ${DATA_GID} ${DATA_GROUP} \
    && usermod -aG ${DATA_GROUP} ${NB_USER}

USER ${NB_USER}
