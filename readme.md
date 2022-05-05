# Unixtime Converter Linx Solution

## Description

REST Service that converts a Unixtimestamp to a DateTime and vice versa. 

## Installation

- Built using Linx 6.1.0 ([https://linx.software](https://linx.software))
- Download and install the Linx Designer [https://linx.software/download-linx/](https://linx.software/download-linx/)
- You should receive an email with your license. Paste it into the designer
- Pull the "Linx 6 Solution" folder from the repo

## Usage

1. Open the UnixTimeService.solution file in the Linx 6 Designer
2. Click "Debug" and "Start" to run the RESTHost service locally
3. Browse to any of the URL's from the "GET Methods" section below
4. Use Postman or similar to post the Body Json to the related URL in the "POST Methods" below

## Publishing

To publish your own Unixtime service you need to get a [Linx Server](https://linx.software/pricing/)

## GET Methods

### Unix Timestamp to UTC DateTime (yyyy-MM-dd HH:mm:ss) with string response

http://localhost:5678/UnixTime/fromunix?timestamp=1549892280

Response: "2019-02-11 13:38:00"

### Unix Timestamp to UTC DateTime (yyyy-MM-dd HH:mm:ss) with JSON object response

http://localhost:5678/UnixTime/fromunixtimestamp?unixtimestamp=1549892280

Response: {"Datetime":"2019-02-11 13:38:00"}

### DateTime (multiple formats) to Unix Timestamp with string response

http://localhost:5678/UnixTime/tounix?date=2019/02/11 13:38:00

Response: "1549892280"

### Current DateTime (multiple formats) to Unix Timestamp with string response

http://localhost:5678/UnixTime/tounix?date=now

Response: Current UnixTimeStamp as integer

### Current UnixTimeStamp as integer

DateTime (multiple formats allowed) to Unix Timestamp with JSON object response

http://localhost:5678/UnixTime/tounixtimestamp?datetime=2019/02/11 13:38:00

Response: {"UnixTimeStamp":"1549892280"}

### Current DateTime as UnixTimestamp

http://localhost:5678/UnixTime/tounixtimestamp?datetime=now

Response: {"UnixTimeStamp":"1549971762"}

## POST Methods

### Unix Timestamp to DateTime with timezone (yyyy-MM-dd'T'HH:mm:ssXXX)
http://localhost:5678/UnixTime/fromunixtimestamp

Body Example 1: {"UnixTimeStamp": "1589772280","Timezone": ""}

Response: {"Datetime":"2020-05-18T03:24:40Z"}

Body Example 2: {"UnixTimeStamp": "1589772280","Timezone": "+3"}

Response: {"Datetime":"2020-05-18T06:24:40+03:00"}

### DateTime (multiple formats) to Unix Timestamp

http://localhost:5678/UnixTime/tounixtimestamp

Body Example 1: {"Datetime": "2019/02/11 13:38:00"}

Response: {"UnixTimeStamp":"1549892280"}

Body Example 2: {"Datetime": "2019-03-13 16:00:00"}

Response: {"UnixTimeStamp":"1552492800"}

## Errors (400)

http://localhost:5678/UnixTime/fromunixtimestamp?unixtimestamp=-99999999991

Response: {"Error":"Operation: Message"}
