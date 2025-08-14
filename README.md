This system monitor will continuously monitor the CPU, memory, and disk usage of your Linux system and display the usage percentages. If any of the thresholds for CPU, memory, or disk usage are exceeded, an alert will be sent. You can customise the threshold values as per your requirements and add your own logic to send alerts.

To save the system_monitor.sh file, 
  - press esc key
  - press colon key :
  - type wq and hit enter key on your keyboard

**The Bash script continuously monitors CPU, memory, and disk usage, sending alerts if usage exceeds specified thresholds. Here's a breakdown of how it works:**

#!/bin/bash: This line specifies that the script will be interpreted using the Bash shell.
CPU_THRESHOLD=80: Sets the CPU usage threshold to 80%. You can adjust this value later.
MEMORY_THRESHOLD=80 and DISK_THRESHOLD=80: Similarly, these define thresholds for memory and disk usage.

send_alert: The function takes two arguments:
$1 represents the resource type (e.g., CPU, Memory, Disk).
$2 represents the current usage percentage.
tput setaf 1: Changes the text color to red to make alerts visually distinct.
tput sgr0: Resets the text formatting to normal after the alert message.

while true; do 
This creates a loop that runs indefinitely.



top -bn1: Runs the top command in batch mode for one iteration to fetch real-time CPU stats.
grep "Cpu(s)": Filters the output to focus on the CPU usage line.
awk '{print $2+$4}': Extracts and sums the percentages of user and system CPU usage.
cpu_usage=${cpu_usage%.*}: Strips the decimal part to simplify threshold comparisons.
if ((cpu_usage >= CPU_THRESHOLD)): Compares the CPU usage with the threshold and calls send_alert if it’s exceeded.

free: Provides memory usage stats.
awk '/Mem/ {printf("%3.1f", ($3/$2) * 100)}': Calculates the percentage of memory in use by dividing used memory ($3) by total memory ($2).
The script compares memory_usage with the threshold and sends an alert if necessary.

df -h /: Fetches disk usage stats for the root directory.
awk '/\// {print $(NF-1)}': Extracts the usage percentage column.
disk_usage=${disk_usage%?}: Removes the % symbol for easier comparisons.
Alerts are triggered if the disk usage exceeds the threshold.

Clears the terminal and displays current resource usage.
sleep 2: Pauses for 2 seconds before the next iteration.


