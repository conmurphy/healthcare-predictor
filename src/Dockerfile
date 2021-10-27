# Use alpine-python-3 appd image
#FROM rtortori/ubuntu-python3
FROM python:3.9

# Set the working directory to /
WORKDIR /

# Copy app requirements
ADD requirements.txt titanic_dataset.csv /

# Optionally define proxy environment
#ARG http_proxy=http://proxy-wsa.esl.cisco.com:80
#ARG https_proxy=http://proxy-wsa.esl.cisco.com:80

# Install requirements
RUN pip install -r requirements.txt 
RUN pip install -U appdynamics

# Set Entry point
#ENV APP_ENTRY_POINT "python /predictor.py"

RUN mkdir /predictor

# Copy app requirements
COPY predictor.py /predictor
COPY utils.py /predictor

# Expose port 5001
EXPOSE 5001/tcp

WORKDIR /predictor

# Run it
#ENTRYPOINT ["./start_with_appd.sh"]
ENTRYPOINT ["python", "predictor.py"]