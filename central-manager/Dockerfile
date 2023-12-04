FROM almalinux:9.2

# Dependencies
RUN dnf -y install wget

# Install yum repository
RUN dnf -y install https://research.cs.wisc.edu/htcondor/repo/23.0/htcondor-release-current.el9.noarch.rpm

# Import signing key
RUN wget https://research.cs.wisc.edu/htcondor/repo/keys/HTCondor-23.0-Key && rpm --import HTCondor-23.0-Key

# Install HTCondor
RUN dnf -y install condor

COPY condor_config.local /etc/condor/
COPY central-manager /etc/condor/config.d
COPY docker-entrypoint.sh /
ENTRYPOINT ["/docker-entrypoint.sh"]
