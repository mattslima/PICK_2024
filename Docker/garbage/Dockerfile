FROM cgr.dev/chainguard/go:latest-dev as buildando
WORKDIR /app
COPY . ./
RUN go mod init hello
RUN go build -o /app/hello

FROM alpine:3.19.1
COPY --from=buildando /app/hello /app/hello
ENV APP="Hello-World"
ARG GIROPOPS="strigus"
ENV GIROPOPS=$GIROPOPS

VOLUME /app/dados

RUN echo "TESTE DO $GIROPOPS"
CMD ["/app/hello"]

 


