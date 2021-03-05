FROM python:slim-buster

ENV PYTHONUNBUFFERED 1

ENV PYTHONDONTWRITEBYTECODE 1

ENV PATH="/home/teste/.local/bin:${PATH}"

RUN adduser teste

USER teste

WORKDIR /home/teste/app

COPY --chown=teste:teste requirements.txt .

RUN pip install --user --upgrade pip -r requirements.txt
