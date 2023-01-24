# Unixtime Converter Linx Solution

## Description

REST Service that converts a Unixtimestamp to a DateTime and vice versa. 

## Installation

- Built using Linx 6.1.0 ([https://linx.software](https://linx.software))
- Download and install the Linx Designer [https://linx.software/download-linx/](https://linx.software/download-linx/)
- Pull the "Linx 6 Solution" folder from the repo

## Usage

1. Open the UnixTimeService.solution file in the Linx 6 Designer
2. Click "Debug" and "Start" to run the RESTHost service locally
3. Browse to any of the URL's from the "GET Methods" section below
4. Use Postman or similar to post the Body Json to the related URL in the "POST Methods" below

## GET Methods

### fromunix

Unix Timestamp to UTC DateTime (yyyy-MM-dd HH:mm:ss) with string response

Request Example: http://localhost:5678/UnixTime/fromunix?timestamp=1549892280<br>
Response: "2019-02-11 13:38:00"

### fromunixtimestamp

Unix Timestamp to UTC DateTime (yyyy-MM-dd HH:mm:ss) with JSON object response

Request Example: http://localhost:5678/UnixTime/fromunixtimestamp?unixtimestamp=1549892280<br>
Response: {"Datetime":"2019-02-11 13:38:00"}

### tounix (with date)

DateTime (multiple formats) to Unix Timestamp with string response

Request Example: http://localhost:5678/UnixTime/tounix?date=2019/02/11 13:38:00<br>
Response: "1549892280"

### tounix (now)

Current DateTime (multiple formats) to Unix Timestamp with string response

Request Example: http://localhost:5678/UnixTime/tounix?date=now<br>
Response: Current UnixTimeStamp as integer

### tounixtimestamp (with date)

DateTime (multiple formats allowed) to Unix Timestamp with JSON object response

Request Example: http://localhost:5678/UnixTime/tounixtimestamp?datetime=2019/02/11 13:38:00<br>
Response: {"UnixTimeStamp":"1549892280"}

### tounixtimestamp (now)

Current DateTime as UnixTimestamp

Request Example: http://localhost:5678/UnixTime/tounixtimestamp?datetime=now<br>
Response: {"UnixTimeStamp":"1549971762"}

## POST Methods

### fromunixtimestamp

Unix Timestamp to DateTime with timezone (yyyy-MM-dd'T'HH:mm:ssXXX)

http://localhost:5678/UnixTime/fromunixtimestamp

Body Example 1: {"UnixTimeStamp": "1589772280","Timezone": ""}<br>
Response: {"Datetime":"2020-05-18T03:24:40Z"}

Body Example 2: {"UnixTimeStamp": "1589772280","Timezone": "+3"}<br>
Response: {"Datetime":"2020-05-18T06:24:40+03:00"}

### DateTime (multiple formats) to Unix Timestamp

http://localhost:5678/UnixTime/tounixtimestamp

Body Example 1: {"Datetime": "2019/02/11 13:38:00"}<br>
Response: {"UnixTimeStamp":"1549892280"}

Body Example 2: {"Datetime": "2019-03-13 16:00:00"}<br>
Response: {"UnixTimeStamp":"1552492800"}

## Errors (400)

http://localhost:5678/UnixTime/fromunixtimestamp?unixtimestamp=-99999999991<br>
Response: {"Error":"Operation: Message"}

## Publishing

Publishing this service requires a [Linx Server](https://linx.software/pricing/)
