# Use an official Python runtime as a parent image
FROM python:3.9.11

ENV PYTHONUNBUFFERED 1

RUN apt-get update
RUN apt-get install postgresql-client -y

WORKDIR /sheepfish_vpn

COPY requirements.txt /sheepfish_vpn/
RUN pip install -r requirements.txt

COPY . /sheepfish_vpn/

# Expose the port that the application will run on
EXPOSE 8000

# Start the application
CMD ["python", "sheepfish_vpn/manage.py", "runserver", "0.0.0.0:8000"]
