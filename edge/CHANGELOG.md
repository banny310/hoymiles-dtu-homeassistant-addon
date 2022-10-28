# CHANGELOG

## 0.9.6
    - default config update

## 0.9.5
    - stability improvements

## 0.9.4
    - [breaking change] structure of config change because ha limits max depth to 2

## 0.9.3
    - [breaking change] pull_interval now is in seconds (instead of mills)
    - fixed ability to override each config record

## 0.9.2
    - hotfix in start script

## 0.9.1
    - hotfix in start script

## 0.9.0
    - proper stop after error
    - ability to override each config record

## 0.8.0
    - discard metrics older than 5 minutes

## 0.7.2

    - fixes in time conversion

## 0.7.1

    - message time in logs (preparation to filter old messages)

## 0.7.0

    - improvements in automatic reconnections

## 0.6.0

    - added watchdog for DTU communication

## 0.5.0

    - fixes for multi packet configurations

## 0.4.1

    - fix in 0 power for large installations

## 0.4.0

    - major architecture change to challenge disconnections from DTU

## 0.3.2

    - fexes in reconnection

## 0.3.1

    - automatic reconnection on connection lost

## 0.3.0

    - support for new message

## 0.2.0

    - many small improvements

## 0.1.9

    - fixes in autodiscovery

## 0.1.8

    - migrate ha autodiscovery twig to POJO model

## 0.1.7

    - fixes in message logging

## 0.1.6

    - fixes in config

## 0.1.5

    - fixes in connectivity and autoreconnect
    - passive mode is now default

## 0.1.4
 
    - Fixes in pooling data

## 0.1.3

    - Fixes in docker run script

## 0.1.2

    - Initial version
