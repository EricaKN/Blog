---
title: "Systemd_alarm_ntfy"
date: 2024-08-22T19:14:46Z
draft: true
---

# INTRODUCTION
Despite the gigantic discussion between lovers and haters of systemd, it is the
current (2024) init system in many Linux OS, and this post is for those who want
to start to get your hands dirty with the service manager. 

# DRAFT
The idea is to set an alarm in your computer which will send a message for your
cellphone.

We can use a simple bash script to create the alarm, our use the "time"
configuration of systemd.

The alarm will run in the
background (as a service) and the ntfy sends the message for a specific channel
created from your
cellphone.

To do so we must:
- Download ntfy app at our cellphone;
- Create a topic with a non-trivial name (because we will create a public topic);
- Create a configuration file for our service;
- Create a bash script for our alarm / Create a ".time" file for our service;

# Download ntfy app at our cellphone
Download the app "ntfy - PUT/POST to your phone".

# Create a topic with a non-trivial name
After installed the ntfy app, you must subscribe to the topic you will send the
notification. 
Create the topic-name and add subscribe. 

# [OPTION 1 - Create your own bash script to run a customized alarm]
# Create a configuration file for our service
Create the file "alarm.sh" at your "/etc/systemd/system/" directory.
On this file we must to add, at least, the [Unit] and [Service] section.

```
[Unit]
Description=My alarm service

[Service]
ExecStart=usr/bin/bash /path/to/the/alarm.sh
User=user
```

# Create a bash script for our alarm
Create a bash script inside your alarm directory.

```
#!/bin/bash

alarm_time="HH:MM:SS" 
alarm_time_sec=$(echo "$alarm_time" | awk -F: '{print($1*3600+$2*60+$3)}')

now=$(date +%H:%M:%S)
now_sec=$(echo "$now" | awk -F: '{print($1*3600+$2*60+$3)}')

sleep_sec=$(($alarm_time_sec - $now_sec))
sleep $sleep_sec && curl -d "TRIM-TRIM! Alarm Alert! It's ${alarm_time}!"
ntfy.sh/<topic_name>

echo "Alarm set to ${alarm_time}!"

```

# [OPTION 2 - Create a simple time configuration from systemd]

