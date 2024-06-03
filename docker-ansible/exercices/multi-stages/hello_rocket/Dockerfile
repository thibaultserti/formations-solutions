FROM rust:latest AS builder

WORKDIR /app
COPY . .

RUN cargo build --release


FROM gcr.io/distroless/cc-debian12

WORKDIR /app
COPY --from=builder /app/target/release/hello_rocket .

ENV ROCKET_ADDRESS=0.0.0.0
ENV ROCKET_PORT=8000
EXPOSE 8000

CMD ["./hello_rocket"]