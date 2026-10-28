FROM python:3.13.9-slim-bookworm

WORKDIR /app

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

RUN groupadd --system --gid 10001 festpass \
    && useradd --system --uid 10001 --gid festpass --create-home festpass

COPY requirements.txt .
RUN pip install --no-cache-dir --upgrade pip \
    && pip install --no-cache-dir -r requirements.txt

COPY app.py .

USER 10001:10001

EXPOSE 5000

CMD ["python", "app.py"]
