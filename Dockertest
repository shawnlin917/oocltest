FROM python:3.8-buster

RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

#Debian 10
RUN curl https://packages.microsoft.com/config/debian/10/prod.list > /etc/apt/sources.list.d/mssql-release.list

RUN exit
RUN apt-get update
RUN ACCEPT_EULA=Y apt-get install gcc libc-dev g++ libffi-dev libxml2 msodbcsql17
# # optional: for unixODBC development headers
RUN apt-get install unixodbc-dev

RUN pip install --upgrade pip

# install SQL Server Python SQL Server connector module - pyodbc
RUN pip install pyodbc

# # install selenium
RUN pip install pandas
RUN pip install selenium
RUN pip install pyodbc
RUN pip install requests

RUN apt-get update && apt-get install -yq chromium

# Install chromedriver for Selenium
RUN wget -q "https://chromedriver.storage.googleapis.com/78.0.3904.70/chromedriver_linux64.zip" -O /tmp/chromedriver.zip \
    && unzip /tmp/chromedriver.zip -d /usr/bin/ \
    && rm /tmp/chromedriver.zip

ADD . /WebScraping
WORKDIR /WebScraping

CMD [ "python", "./_init_.py" ]
