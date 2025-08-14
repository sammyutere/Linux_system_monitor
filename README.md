This system monitor will continuously monitor the CPU, memory, and disk usage of your Linux system and display the usage percentages. If any of the thresholds for CPU, memory, or disk usage are exceeded, an alert will be sent. You can customise the threshold values as per your requirements and add your own logic to send alerts.

To save the system_monitor.sh file, 
  - press esc key
  - press colon key :
  - type wq and hit enter key on your keyboard

*What Does the Code in System_monitor.sh do?*

#!/bin/bash: This line specifies that the script will be interpreted using the Bash shell.
CPU_THRESHOLD=80: Sets the CPU usage threshold to 80%. You can adjust this value later.
MEMORY_THRESHOLD=80 and DISK_THRESHOLD=80: Similarly, these define thresholds for memory and disk usage.

