Provide your solution here:
The scenarios which cause NGINX load balancer VM  consistently running at 99% memory usage would be as below:

1. High traffics comming to the NGINX load balancer
* The incomming traffic could be huge that exceed the current memory setup, could be due to real traffic or DDOS attach, etc -> not likely to usually happen with the current huge memory allocation
Trouble shooting:
* Check log, log files size to see the frequency of requests, and the log pattern to see if something abnormal
* use free -m command to check the memory usage
* If prometheus and grafana is installed, check the metrics (number of requests, errors rate,...)
Solution:
* Temporary: Increase the memory to avoid service interuption
* Long term: Analyze  the real rootcause, implement a sustainable solution to avoid it happening in the future

2. Memory Leaks issue on nginx proxy
Troubleshooting:
* Check the nginx version, release/upgrade date, release note to see if any known issue is happening with current version
Solution:
Upgrade/Downgrade to stable nginx version

3. Full VM storage
Sometime storage full because of log can also cause nginx cannot write more log, causing request hanging  which make the memory utilization go high

Troubleshooting:
* Check the storage usage on the VM
* Check nginx log size 
Solution:
* Increase storage
* Remove unuse, log archive log file, unuse files to release the storage
