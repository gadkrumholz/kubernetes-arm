FROM ubuntu:bionic

RUN apt-get update && apt-get install -y wget && wget http://ports.ubuntu.com/pool/universe/n/nmap/ncat_7.80+dfsg1-2build1_arm64.deb && apt-get install -y ./ncat_7.80+dfsg1-2build1_arm64.deb && apt-get install -y mysql-client percona-xtrabackup && rm -rf /var/lib/apt/lists/*

CMD bash
