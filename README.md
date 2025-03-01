# lab4Dec2021

LoadAverage15m Runbook

## Description
===========



LoadAverage15m message means that the CPU load average as reported by the OS over the last 15 minutes.
In a simple language you might have a performance problem (it depends).

The average load means that in a unit time, the system is inRunnable stateandUninterruptible stateAverage number of processes, 
abbreviated asAverage number of active processe. It is not directly related to CPU utilization (that what "depends" means).

## Where to start.
===========

If the CLI is available you can run the top utility.

The top utility gives you a real-time look at what’s going on with the server. By default, when top starts, it shows activity for all CPUs. 
This view can be changed by pressing the numeric 1 key, which adds more detail regarding the usage values for each CPU.

Alternatively, you can use the following command to get the running process and blocking process. 
It should be the same as the load average.

```sh
ps -eo s,user,cmd | grep ^[RD] |wc -l
```

Additionally, you can run the following command to list the current number of threads in these states including the process/program name too:

```sh
ps -eo s,user,cmd | grep ^[RD] | sort | uniq -c | sort -nbr | head -20
```

Depending on the reason/process which causes a high level workload of the CPU you can kill pending processes, restart product, or add more CPU/cores.

For the reference, the [following article](https://www.brendangregg.com/blog/2017-08-08/linux-load-averages.html) provides some facinating insights on the origination of this issue.
