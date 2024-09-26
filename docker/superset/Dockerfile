FROM apache/superset:latest

USER root

ENV SUPERSET_CONFIG_PATH="/app/superset_config.py"
ENV ADMIN_USERNAME="admin"
ENV ADMIN_EMAIL="admin@superset.com"
ENV ADMIN_PASSWORD="admin"

RUN pip install trino sqlalchemy-trino

COPY superset-init.sh /superset-init.sh

COPY superset_config.py /app/
RUN echo "SECRET_KEY = '$(openssl rand -base64 42)'" >> /app/superset_config.py

USER superset
CMD ["bash", "/superset-init.sh"]