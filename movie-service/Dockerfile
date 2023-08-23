FROM python:3.8 as base

ENV PYTHONFAULTHANDLER=1 \
  PYTHONUNBUFFERED=1 \
  PYTHONHASHSEED=random 

WORKDIR /code

RUN pip install "poetry==1.5.1"

COPY . .

EXPOSE ${PORT}

RUN poetry config installer.max-workers 1

FROM base AS dev

RUN poetry install --no-interaction --no-ansi

FROM base AS prod

RUN poetry install --without dev --no-interaction --no-ansi

