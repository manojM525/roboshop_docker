FROM python:3.9-slim

WORKDIR /app

EXPOSE 8080

COPY requirements.txt .

RUN apt-get update && apt-get install -y \
        build-essential \
        python3-dev \
        libpcre3-dev \
    && pip install --no-cache-dir -r requirements.txt \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

COPY *.py .
COPY payment.ini .

# create application user
RUN useradd -r -u 1001 roboshop

# change ownership
RUN chown -R roboshop:roboshop /app

# switch to non-root user
USER roboshop

CMD ["uwsgi", "--ini", "payment.ini"]