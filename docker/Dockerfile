# Dockerfile
# Note: Make sure that your Dockerfile and requirements.txt are in the root directory.

FROM python:3.8-slim-buster
WORKDIR /nhl-analyzer
COPY nhl/requirements.txt nhl/requirements.txt
RUN /usr/local/bin/python -m pip install --upgrade pip
RUN pip3 install -r requirements.txt
COPY . .
CMD ["python3", "-m", "streamlit", "run", "app.py"]