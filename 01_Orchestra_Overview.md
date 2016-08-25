# Harvard Medical School [Research Computing](https://rc.hms.harvard.edu/#)
*based on the [Orchestra Wiki New User Guide](https://wiki.med.harvard.edu/Orchestra/NewUserGuide) by Kristina Holton*

## Software

Licensed software can be found [here](https://wiki.med.harvard.edu/Software/)

## Orchestra 
*Shared high-performance computing cluster*

* over 5,000 compute cores
* petabytes of data storage
* supports next-gen data analysis

*Every user gets a home directory and access to /n/scratch2/*

* home directory size: 100 GB
* /n/scratch2/ size: 5TB
* /n/scratch2/ files are **deleted after 15 days**

For questions, contact: <rchelp@hms.harvard.edu>

### Set up


To login: 

	ssh username@orchestra.med.harvard.edu

To copy files: 

	scp username@orchestra.med.harvard.edu:/path/to/file-to-copy /path-to-location-to-copy-to

To see which modules are available:

	module avail
	
To load a module: 

	module load module-name
	
To check which module is running:

	which module-name
	
To unload a module: 

	module unload module-name
	
To automatically load modules when you log in, alter your `.bashrc` file to include `module load null` and then: 

	module initadd module-name
	
### Load sharing facility (LSF)
*System for ensuring that users fairly share the processors and memory in the Orchestra cluster*

* Assigns importance to individual users as shares
* Individuals with the more shares are higher priority
* Individuals with equal shares are treated on a first-come, first-serve basis

**User priority increases when using less than the assigned fair share of the cluster**

*See [LSF manual](https://wiki.med.harvard.edu/doc/lsf/admin/fairshare.html) for additional information*


To submit jobs to LSF: 

	bsub < job.sh
	
Where the `job.sh` script contains the following information: 

	#!/bin/bash
	#BSUB -n 1						#number of cores is 1
	#BSUB -W 01:00					#runlimit is 1h
	#BSUB -J myjob					#name the job myjob
	#BSUB -o %J.out					#send screen output to file
	#BSUB -e %J.err					#send errors to file
	#BSUB -N						#receive an email when the job finishes
									#email is sent to address specifid in the file ~/.forward
	#BSUB -q short					#submit to "short" queue
	#BSUB -R "rusage[mem=8000]"		#requesting over 2GB memory
									## do not request beyond 90GB RAM
	./a.out							#run the commands in this script
	
To start an interactive session: 

	bsub -Is -q interactive bash

To check which queues you have access to: 

	bqueues -u username

Selecting queue: 

* For one or two jobs, select `priority`
* For multi-core jobs, select `mcore`
* For 3 or more jobs taking <12h each, select `short`
* For 3 or more jobs taking >12h each, select `long`

To check the status of your jobs:

	bjobs

To terminate a job: 

	bkill jobID

To see why job is pending: 

	bjobs -l jobID
	
Check out [Troubleshooting Jobs](https://wiki.med.harvard.edu/Orchestra/TroubleshootingLSFJobs) if in trouble


### Copying files

1. Download [FileZilla](http://filezilla-project.org/)
2. Enter the following connection parameters: 
	* host: orchestra.med.harvard.edu
	* port: 22 (SCP/SFTP port)
	* username
	* password

	
For additional help, see the [Orchestra Wiki](https://wiki.med.harvard.edu/Orchestra/NewUserGuide)

### xQuartz forwarding
System for visualizing graphics while working in terminal.
[Download xQuartz for Mac](https://www.xquartz.org/)

To enable X11 forwarding for 1 session: 

	ssh -X username@orchestra.med.harvard.edu
	
To enable X11 forward by default, add the following to the `~/.ssh/config` file: 

	Host orchestra.med.harvard.edu
	ForwardX11 Yes
	


*X11 is disabled by default in SSH clients because the remote hosts can view your X11 server*

### Retrieving backups 
Home directory backups are stored for **60 days**

	cd .snapshot
	cp file-from-snapshot to-destination


For more information check out the [Orchestra Wiki](https://wiki.med.harvard.edu/Orchestra/WebHome)

### Citing orchestra

Portions of this research were conducted on the Orchestra High Performance Compute Cluster at Harvard Medical School. This NIH supported shared facility consists of thousands of processing cores and terabytes of associated storage and is partially provided through grant NCRR 1S10RR028832-01. See <http://rc.hms.harvard.edu> for more information.
