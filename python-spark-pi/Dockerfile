FROM gcr.io/datamechanics/spark-py-connectors:3.0.0-dm4

ENV PYSPARK_MAJOR_PYTHON_VERSION=3

WORKDIR /opt/application/

COPY requirements.txt .
RUN pip3 install -r requirements.txt

COPY src/ src/

COPY pi.py .
