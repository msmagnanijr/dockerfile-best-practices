FROM python:3.9

RUN apt-get update && apt-get install gcc -y && apt-get clean

RUN adduser --disabled-password --gecos '' clouduser

USER clouduser

WORKDIR /home/clouduser

COPY --chown=clouduser requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]