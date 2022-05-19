FROM python:3.9.12-slim-bullseye as build

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

FROM python:3.9.12-slim-bullseye as runtime

COPY --from=build /home/clouduser /app

COPY --from=build /home/clouduser/.local/lib/python3.9/site-packages /usr/local/lib/python3.9/site-packages

WORKDIR /app

ENV PYTHONPATH=/usr/local/lib/python3.9/site-packages

CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]