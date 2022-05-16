FROM python:3.9.12-slim-bullseye@sha256:4277d13b9392a5669cdff5455b6a8d5bb7c36756f575f5192139cf9b9add018c AS build

ADD . /app
WORKDIR /app

RUN pip install --upgrade pip
RUN pip install -r ./requirements.txt

FROM gcr.io/distroless/python3@sha256:d1cf638027d12a035d3c2a574dddc8efcb8aed6a5143a7bd5b24204f3ce91cd6 as runtime

COPY --from=build /app /app

COPY --from=build /usr/local/lib/python3.9/site-packages /usr/local/lib/python3.9/site-packages

WORKDIR /app

ENV PYTHONPATH=/usr/local/lib/python3.9/site-packages

EXPOSE 5000

CMD ["app.py"]