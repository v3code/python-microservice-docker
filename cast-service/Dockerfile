FROM python:3.8 as base

WORKDIR /code

ENV PYTHONFAULTHANDLER=1 \
  PYTHONUNBUFFERED=1 \
  PYTHONHASHSEED=random 

RUN pip install "poetry==1.5.1"

COPY . .

RUN poetry config installer.max-workers 1

EXPOSE ${PORT}

FROM base AS dev

# WORKDIR /code

RUN poetry install --no-interaction --no-ansi


FROM base AS prod

# WORKDIR /code

RUN poetry install --without dev --no-interaction --no-ansi
