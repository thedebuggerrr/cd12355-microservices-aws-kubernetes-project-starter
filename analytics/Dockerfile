FROM public.ecr.aws/docker/library/python:3.9-slim

WORKDIR /app

RUN apt-get update -y && \
    apt-get install -y build-essential libpq-dev && \
    rm -rf /var/lib/apt/lists/*

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 5153

CMD ["python", "app.py"]
