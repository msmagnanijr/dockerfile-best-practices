FROM python:3.9.12-slim-bullseye AS build

ADD . /app
WORKDIR /app

RUN pip install --upgrade pip
RUN pip install -r ./requirements.txt


FROM gcr.io/distroless/python3:nonroot as runtime

COPY --from=build /app /app

COPY --from=build /usr/local/lib/python3.9/site-packages /usr/local/lib/python3.9/site-packages

WORKDIR /app

ENV PYTHONPATH=/usr/local/lib/python3.9/site-packages

EXPOSE 5000

CMD ["app.py"]