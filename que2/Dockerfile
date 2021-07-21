FROM python:alpine

WORKDIR /home/app

ADD requirements.txt .
RUN pip install -r requirements.txt

ADD app.py .

EXPOSE 80

CMD [ "python", "app.py" ]