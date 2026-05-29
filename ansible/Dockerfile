FROM python:3.12-slim
# RUN groupadd -r ansible-runner && \
#     useradd -r -g ansible-runner -m ansible-runner
# RUN mkdir -p /home/ansible-runner/.ssh && \
#     chmod 700 /home/ansible-runner/.ssh && \
#     chown -R ansible-runner:ansible-runner /home/ansible-runner/.ssh
RUN apt update && apt install -y openssh-client
RUN pip install --no-cache-dir ansible==13.7
RUN ansible-galaxy role install geerlingguy.docker,8.0.0
WORKDIR /ansible
# USER ansible-runner
ENTRYPOINT ["ansible-playbook"]
