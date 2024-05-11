FROM python:3.12-alpine AS builder

RUN apk add --no-cache gcc musl-dev libffi-dev openssl-dev
WORKDIR /build
COPY requirements.txt .
RUN pip install --prefix="/install" -r requirements.txt


FROM python:3.12-alpine

RUN adduser --disabled-password --gecos "" --home "/nonexistent" --shell "/sbin/nologin" --no-create-home "app"

COPY --from=builder /install /usr/local
WORKDIR /app
COPY . .
USER app:app
ENTRYPOINT [ "uvicorn", "main:app", "--host", "0.0.0.0" ]
