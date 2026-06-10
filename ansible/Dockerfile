FROM python:3.12-slim
RUN apt update && apt install -y openssh-client vim
RUN pip install --no-cache-dir ansible==13.7
RUN ansible-galaxy role install geerlingguy.docker,8.0.0 && \
    ansible-galaxy collection install prometheus.prometheus:0.30.0
WORKDIR /ansible

