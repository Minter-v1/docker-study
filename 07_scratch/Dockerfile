FROM golang:alpine AS builder
WORKDIR /app
COPY main.go .
RUN CGO_ENABLES=0 GOODS=linux go build -a -installsuffix cgo -o helloworld main.go

FROM scratch
COPY --from=builder /app/helloworld .
EXPOSE 8080
ENTRYPOINT [ "./helloworld" ]