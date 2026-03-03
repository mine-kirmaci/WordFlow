# Temel Image 
FROM python:3.11-slim

# Sistem Bağımlılıkları 
RUN apt-get update && apt-get install -y \
    curl \
    gcc \
    && rm -rf /var/lib/apt/lists/*

# Çalışma Dizini 
WORKDIR /app

# Bağımlılıkları Yükle 
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
#               └── pip'in kendi cache'ini kullanma → image küçük kalır

# Uygulama Kodunu Kopyala 
COPY . .

# Ortam Değişkenleri 
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Varsayılan Komut 
CMD ["pytest", "tests/", "-v", "--cov=lambda", "--cov-report=term"]