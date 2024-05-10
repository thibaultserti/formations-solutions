FROM golang AS builder

WORKDIR /app
COPY . .
RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app .


FROM scratch

WORKDIR /
COPY --from=builder /app/app .

ENV PORT 8080
ENV HELLO_MSG Hello
CMD ["/app"]
