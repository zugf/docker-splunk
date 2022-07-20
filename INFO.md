make splunk-debian-10 -n

docker build  --build-arg SCLOUD_URL=https://github.com/splunk/splunk-cloud-sdk-go/releases/download/v1.11.1/scloud_v7.1.0_linux_amd64.tar.gz -t base-debian-10:"latest" ./base/debian-10
if [ -d "splunk-ansible" ]; then \
        echo "Ansible directory exists - skipping clone"; \
else \
        git clone https://github.com/splunk/splunk-ansible.git --branch develop; \
fi
cd splunk-ansible && git rev-parse HEAD > version.txt
cat splunk-ansible/version.txt
docker build  \
        -f splunk/common-files/Dockerfile \
        --build-arg SPLUNK_BASE_IMAGE=base-debian-10 \
        --build-arg SPLUNK_BUILD_URL=https://download.splunk.com/products/splunk/releases/8.2.6/linux/splunk-8.2.6-a6fe1ee8894b-Linux-x86_64.tgz \
        -t splunk-debian-10:"latest" .

 id -u username

https://github.com/splunk/docker-splunk/issues/265

```sh
docker build  \
        -f splunk/common-files/Dockerfile \
        --build-arg UID=1000 --build-arg GID=1000 \
        --build-arg SPLUNK_BASE_IMAGE=base-debian-10 \
        --build-arg SPLUNK_BUILD_URL=https://download.splunk.com/products/splunk/releases/8.2.6/linux/splunk-8.2.6-a6fe1ee8894b-Linux-x86_64.tgz \
        -t splunk-debian-10:8.2.6 .
```



8.2.6 commit: 071c8ac6d8dadccb0d7e6d9ee6c85bf2ffb63a92