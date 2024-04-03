FROM cgr.dev/chainguard/python:latest-dev as builder
WORKDIR /app
COPY requirements.txt .
RUN python -m venv venv && \
    . venv/bin/activate && \
    pip install --no-cache-dir -r requirements.txt && \
    pip install flask && \
    pip install --upgrade flask

FROM cgr.dev/chainguard/python:latest
WORKDIR /app
COPY --from=builder /app/venv /app/venv
COPY . .
ENV PATH="/app/venv/bin:${PATH}" \
    REDIS_HOST="localhost"
EXPOSE 5000
ENTRYPOINT ["flask", "run", "--host=0.0.0.0"]

