# Monitoring - task2

For a server which is doing SSL offloading the most important metrics to monitor are:

## Operating system:

- CPU 
- Connection count (open connection)
- Bandwidth usage
- Memory
- Number of processes

## Proxy server:

- Inbound traffic
- Outbound traffic
- RTT (round-trip time) 

### CPU

- SSL Offloading is cpu sensitive process.
- User - ssh connections, databases (anything not a part of OS or hardware) - shows the useful CPU usage
- System - kernel (network packets are inspected by the kernel - firewall works on the kernel)
- IO - CPU priority by default
- nice - usage of cpu above normal treshold

### Connection count

Health indicator - too many or too little connections can signal something requires attention (for instance DDOS attack)

### Bandwidth usage

Prevent bandwidht saturation which could lead to timeouts, dropped connections.

### Memory

Keeping workload in RAM to avoid slowdowns if workload is moved to swap. Detecting memory leaks, hung processes.

### Number of processes

In correlation with memory usage detection of hung and zombie processes

### Inbound and outbound traffic

The balance between inbound and outbound connections should be monitored and maintained. Having an imbalance between the two could be the indicator of an attack or malfunction. 

### RTT

Latency monitoring. Could indicate slowness in the whole chain from request to reply (ex. overload of this server or overload on backen or db server, slow network).


## How to monitor the metrics:

### Vmstat
Memory monitoring
### Iostat
IO monitoring
### Mpstat
CPU monitoring

Each of these tools is able to monitor only one aspect of our system. The challenge is to combine them, to present stats in human readable form and to archive them (they show only "right-now" result) - the problem is to store them and agregate them in order to present the general view of the server performance

### NMON:

Combines stats, but is not showing the trend, requires additional visualisation tool

### NAGIOS/CENTREON/ZABBIX:

They are complex tools with build-in visualisation. Can monitor system stats and application stats at the same time and present them in different ways that could help to understand problems (different dashboards, graphs...) that can show show different aspects of one KPI. They are complex, require their own infrastructure (server-client applications) and must be configured for specific task. 

### Datadog/Dynatrace

They are able to collect all stats and display them in graphical way, but they are mostly geared towards application development and analyses of its performance before production (Dynatrace requires specific stop points in the application code in order to be used at its maximum).

### Elastic Search Stack/Prometeus,Grafana etc...

Very powerful tools for data analysis, can leverage machine learning and AI. require a lot of processing power, configuration and integration (plugins, agents that you have to unlike in case of above configure to show you what you want to see, otherwise they just grab data but don't present it in a meaningful way).