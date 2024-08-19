FROM python:3.11-slim

ARG APP_HOME=/app

WORKDIR ${APP_HOME}

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONBUFFERED 1

#pip installs all dependencies 
RUN pip install --upgrade pip
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY ./entrypoint /entrypoint
RUN sed -i 's/\r$//g' /entrypoint
RUN chmod +x /entrypoint

COPY ./start /start
RUN sed -i 's/\r$//g' /start
RUN chmod +x /start

#copy app code to WORKDIR
COPY . ${APP_HOME}

ENTRYPOINT [ "/entrypoint" ]