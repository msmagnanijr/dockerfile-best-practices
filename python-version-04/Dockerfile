FROM python:3.9.12-slim-bullseye

RUN apt-get update && apt-get install gcc -y && apt-get clean

RUN adduser --disabled-password --gecos '' clouduser

USER clouduser

WORKDIR /home/clouduser

COPY --chown=clouduser requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

EXPOSE 5000

CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]