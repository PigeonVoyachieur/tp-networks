FROM python:3.11-slim
WORKDIR /usr/src/app
RUN pip install --no-cache-dir Flask pymysql 
COPY app.py .
EXPOSE 5000
CMD ["python", "app.py"]