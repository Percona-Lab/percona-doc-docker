FROM ubuntu:20.04

RUN apt-get update
RUN apt-get install -y software-properties-common
RUN add-apt-repository universe
RUN apt-get install -y git graphviz wget unzip python3 python3-pip python3-dev fontconfig fonts-noto fonts-inconsolata default-jre python3-cairocffi

RUN mkdir -p /usr/share/fonts/chivo && cd /usr/share/fonts/chivo && wget -O Chivo.zip https://fonts.google.com/download?family=Chivo && unzip Chivo.zip
RUN fc-cache -f

WORKDIR /docs
COPY requirements.txt /docs
RUN pip3 install -r requirements.txt

# plantuml: Install local copy (remote access via setting in mkdocs.yml)
RUN mkdir -p /opt/plantuml && cd /opt/plantuml && wget -O plantuml.jar https://downloads.sourceforge.net/project/plantuml/plantuml.jar
COPY plantuml /usr/local/bin
RUN chmod +x /usr/local/bin/plantuml

EXPOSE 8000
CMD ["mkdocs","build"]
