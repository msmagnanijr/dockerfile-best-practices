FROM python:3.9.12-slim-bullseye

RUN apt-get update && apt-get install gcc -y && apt-get clean

RUN adduser --disabled-password --gecos '' clouduser

USER clouduser

WORKDIR /home/clouduser

ENV PYTHONUSERBASE=/home/clouduser/.local
ENV PATH=$PYTHONUSERBASE/bin:$PATH
ENV PIP_USER=yes

COPY --chown=clouduser requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]