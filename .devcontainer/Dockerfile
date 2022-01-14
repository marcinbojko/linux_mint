FROM linuxmintd/mint20.3-amd64:latest as base
ENV version="mint20.3"
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -y mc curl wget tar bzip2 build-essential linux-image-virtual linux-tools-virtual linux-cloud-tools-virtual net-tools openssh-server \
  ca-certificates python3 python3-dev python3-pip python3-wheel libkrb5-dev \
  && /usr/bin/python3 -m pip install --upgrade pip \
  && /usr/bin/python3 -m pip install --upgrade jmespath jsonlint yamllint ansible-core==2.11.7 ansible pywinrm requests-kerberos requests-ntlm requests-credssp pypsrp \
  && /usr/local/bin/ansible-galaxy collection install --upgrade ansible.posix \
  && /usr/local/bin/ansible-galaxy collection install --upgrade community.general \
  && /usr/local/bin/ansible-galaxy collection install --upgrade community.crypto \
  && apt-get clean all -y && rm -rf /var/lib/apt/lists/*