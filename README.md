# Basic-System-Health-Monitoring-with-Python

This project involves a Python script designed to monitor and log the health of a system. The script collects key system metrics, including CPU usage, memory usage, and disk usage, and saves them to a text file. This project demonstrates automation, scripting, and system administration skills.

## Project Description

The script uses the `psutil` library to gather system metrics and logs them with timestamps for future reference. This helps in automating routine monitoring tasks and provides insights into system performance.

## Features

- **System Metrics Monitoring:** Collects CPU, memory, and disk usage statistics.
- **Logging:** Saves metrics to a text file with timestamps.

## Setup and Installation

### Prerequisites

- Python 3.x
- Virtual Environment (recommended)

### Steps

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/yourusername/system-health-monitoring.git
   cd system-health-monitoring

2. **Create a Virtual Environment:**

bash

python3 -m venv myenv
source myenv/bin/activate

3. **Install Dependencies:**
   
pip install psutil

4. **Run the Script:**

python system_health_monitor.py

5. **Check the Log File:**

The log file system_health_log.txt will be created in the same directory as the script.

**Code**

import psutil
import datetime

def log_system_health():
    timestamp = datetime.datetime.now().strftime('%Y-%m-%d %H:%M:%S')
    cpu_usage = psutil.cpu_percent(interval=1)
    memory_usage = psutil.virtual_memory().percent
    disk_usage = psutil.disk_usage('/').percent

    log_entry = (
        f"{timestamp} - CPU Usage: {cpu_usage}%\n"
        f"{timestamp} - Memory Usage: {memory_usage}%\n"
        f"{timestamp} - Disk Usage: {disk_usage}%\n"
    )

    with open("/home/cgoetz/system_health_log.txt", "a") as log_file:
        log_file.write(log_entry)

if __name__ == "__main__":
    log_system_health()

Issues and Resolutions
Issue 1: Installation Errors

Error:

    pip3 install psutil failed with "externally-managed-environment" error.

Resolution:

    Created a virtual environment using python3 -m venv myenv.
    Activated the virtual environment and successfully installed psutil using pip install psutil.

Issue 2: FileNotFoundError

Error:

    FileNotFoundError: [Errno 2] No such file or directory: '/path/to/system_health_log.txt'.

Resolution:

    Changed the log file path to /home/cgoetz/system_health_log.txt to ensure the file location exists.

Issue 3: Permissions and Directory Setup

Error:

    Log file could not be created due to directory issues.

Resolution:

    Created the required directory using mkdir -p /home/cgoetz/ to ensure the log file could be written.
