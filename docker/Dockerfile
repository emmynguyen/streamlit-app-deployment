# Dockerfile
# Note: Make sure that your Dockerfile and requirements.txt are in the root directory.

FROM python:3.8-slim-buster
COPY . /app
WORKDIR /app
# optional: RUN /usr/local/bin/python -m pip install --upgrade pip
RUN pip3 install -r requirements.txt
EXPOSE 80
WORKDIR /app
CMD ["python3", "-m", "streamlit", "run", "app.py"]