FROM karmab/client-python-kubernetes
MAINTAINER Ricardo Katz <ricardo.katz@gmail.com>

EXPOSE 9000

RUN yum -y install epel-release && yum -y install python-pip && yum clean all && rm -rf /var/cache/yum
RUN pip install flask
ADD ui.py /tmp
COPY templates /tmp/templates
COPY static /tmp/static

ENTRYPOINT  ["python", "/tmp/ui.py"]
