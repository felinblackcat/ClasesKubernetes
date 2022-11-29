FROM python:3.10-slim as builder
WORKDIR /usr/src/app
ENV PYTHONDOWNWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
RUN apt-get update && apt-get upgrade -y && apt install --no-install-recommends -y \
    build-essential\
    python-dev\
    libpq-dev
RUN apt-get update && apt install -y --no-install-recommends libpq-dev  && rm -rf /var/lib/apt/lists/*
RUN python3 -m pip install --upgrade pip
RUN pip install --upgrade pip
RUN pip install pip setuptools
RUN python -m venv /opt/venv
# Make sure we use the virtualenv:
ENV PATH="/opt/venv/bin:$PATH"
RUN pip install  \
    Django==4.0.6 \
    djangorestframework==3.13.1 \
    django-cors-headers==3.13.0 \
    psycopg2 \
    gunicorn==20.1.0 \
    python-decouple==3.6 \
    python-dotenv==0.20.0\
    django-cors-headers==3.13.0 --no-cache-dir
FROM python:3.10-slim as Production
WORKDIR /usr/src/app
RUN apt-get update && apt install -y --no-install-recommends libpq-dev  && rm -rf /var/lib/apt/lists/*
COPY --from=builder /usr/src/app /usr/src/app
COPY --from=builder /opt/venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
COPY app /usr/src/app/
CMD ["gunicorn" , "--bind","0.0.0.0:8000", "--reload", "tacho_test.wsgi:application"]