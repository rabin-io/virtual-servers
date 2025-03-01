---

copyright:
  years:  2020, 2021
lastupdated: "2021-05-18"

keywords: monitoring no driver mode, no driver mode, monitoring light, light mode

subcollection: virtual-servers

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}
{:external: .external}

#  {{site.data.keyword.mon_full_notm}} 'no driver mode'
{: #monitoring-light-no-driver}

When you provision an {{site.data.keyword.mon_full_notm}} instance, you can enable the 'no driver mode'. You can access metrics through the pre-built dashboards that are available in the {{site.data.keyword.mon_full_notm}} dashboard.
{: shortdesc}

## Configuring {{site.data.keyword.mon_full_notm}} 'no driver mode'
{: #provision-monitoring-light}

To enable 'no driver mode' and monitor and manage metrics, you need to configure a monitoring agent in each environment that you want to use 'no driver mode'.

Use these steps to enable 'no driver mode'.

1. Provision a Graduated tier Sysdig instance by following the steps in [Provisioning a monitoring instance](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-provision). For more information about the Graduated tier, see [Service plans](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-pricing_plans).
2. Enable {{site.data.keyword.mon_full_notm}} 'no driver mode' by following the steps that correspond to your provisioned environment by following the steps in [Configuring a monitoring agent](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-config_agent).
3. Add the following configuration to the `dragent.yaml` file:

```curl
feature:
  mode: `monitor_light`
  Available options for the feature mode are: `monitor_light | monitor | none`.
```
{: screen}

**OR**

Alternatively, you can use the following curl command:

```text
curl -sL https://ibm.biz/install-sysdig-agent | sudo bash -s -- -a SYSDIG_ACCESS_KEY -c COLLECTOR_ENDPOINT --collector_port 6443 --secure true -ac "feature:\n mode: monitor_light"
```
{: pre}

Where

`SYSDIG_ACCESS_KEY` is the ingestion key for the instance.

`COLLECTOR_ENDPOINT` is the ingestion URL for the region where the monitoring instance is available.

**4.** Restart the agent.

After you complete the previous steps, limited functionality is implemented and you see the reduced pricing on your invoice.
{: note}

### What's next
{: #sysdig-light-whats-next}

After you provision your monitoring agent and enable 'no driver mode', you need to configure a monitoring agent in each environment that you want to monitor. For more information about configuring a monitoring agent, see [Configuring a monitoring agent](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-config_agent).

## {{site.data.keyword.mon_full_notm}} 'no driver mode' metrics
{: #sysdig-light-metrics}

{{site.data.keyword.mon_full_notm}} collects basic virtual server instance metrics such as CPU usage, disk usage, network traffic, and memory. You can access metrics through the prebuilt monitoring dashboard.

Use the following tables to see which metrics are supported by 'no driver mode'.

| Name | Description |
| ----------- | ----------- |
| cpu.cores.used	| CPU core usage |
| cpu.cores.used.percent | CPU core usage percent for each container |
| cpu.idle.percent	| Percentage of time that the CPUs were idle and the system had no outstanding disk I/O requests. |
| cpu.iowait.percent | Percentage of time that the CPUs were idle and the system did an outstanding disk I/O requests |
| cpu.nice.percent	| Percentage of user level CPU usage with 'Nice' priority |
| cpu.stolen.percent | 	Percentage of time that a virtual machine CPU is in a state of involuntary wait because the physical CPU is shared among virtual machines. |
| cpu.system.percent |  Percentage of system level CPU usage  |
| cpu.used.percent	| Percentage of system level CPU usage |
| cpu.user.percent	| Percentage of user level CPU usage |
| load.average.percpu.1m	| Average number of jobs in the CPU run queue or waiting for disk I/O averaged over 1 minute for all cores. |
| load.average.percpu.5m	| Average number of jobs in the CPU run queue or waiting for disk I/O averaged over 5 minutes for all cores.  |
| load.average.percpu.15m	| Average number of jobs in the CPU run queue or waiting for disk I/O averaged over 15 minutes for all cores.  |
| memory.bytes.available	| Available memory |
| memory.bytes.total	| Total memory of a host |
| memory.bytes.used	| Total memory used |
| memory.bytes.virtual	| Physical memory used |
| memory.pageFault.major	| Count of the condition that occurs when a program accesses a memory page that is mapped in the virtual address space, but not loaded in physical memory.  |
| memory.pageFault.minor	| A count of the condition in which a memory page was loaded in memory at the time the page fault was generated, but was not marked in the memory management unit as being loaded in memory. |
| memory.swap.bytes.available	| The swap memory available. Determined by the sum of the free and cached swap memory.|
| memory.swap.bytes.total	| Total amount of swap memory |
| memory.swap.bytes.used	| Amount of swap memory used |
| memory.swap.used.percent	| Percentage of swap memory used |
| memory.used.percent	| Percentage of physical memory in use |
|	file.bytes.in | Bytes read from the file |
|	file.bytes.out | Bytes writtem to the file |
| file.bytes.total	| Total number of bytes written to, and read from, the file  |
|	file.iops.in | File read operations per second |
|	file.iops.out |  File write operations per second |
|	file.iops.total | Total number of file read and write operations per second  |
| file.open.count	| Number of times file was opened |
|	file.time.in | Time reading file |
|	file.time.out | Time writing file |
|	file.time.total | Total time during file I/O |
|	fs.bytes.free | Total number of free bytes |
|	fs.bytes.total | Size of the file system |
|	fs.bytes.used | Total number or bytes used |
|	fs.free.percent | Percentage of file system free |
|	fs.inodes.total.count | Number of inodes in the file system |
|	fs.inodes.used.count | Number of inodes used in the file system |
|	fs.inodes.used.percent | Percentage of file system inodes used |
| fs.largest.used.percent	| Percentage of largest file system |
| fs.root.used.percent	| Percentage of root file system used |
| fs.used.percent	| Percentage of the file system used |
|	net.bytes.in | Inbound network bytes |
|	net.bytes.out | Outbound network bytes |
|	net.bytes.total | Total network bytes |
| proc.count	| Number of processors |
| thread.count	| Number of CPU threads or virtual cores |  
| container.count | Numbers of containers |
| system.uptime	| Total system uptime |
| uptime	| Percentage of time the selected entity or entities was down over the defined time window. |
{: caption="Table 1. Monitoring 'no driver mode' metrics" caption-side="top"}
