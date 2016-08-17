# Harvard Medical School Research Computing
*based on the [Orchestra Wiki New User Guide](https://wiki.med.harvard.edu/Orchestra/NewUserGuide) by Kristina Holton*

## Orchestra 
*Shared high-performance computing cluster*

* over 5,000 compute cores
* petabytes of data storage
* supports next-gen data analysis

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

To submit jobs to LSF: 

	bsub < job.sh
	
Where the `job.sh` script contains the following information: 

	#!bin/bash
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

To check the status of your jobs:

	bjobs

To terminate a job: 

	bkill jobID
	

### Copying files

1. Download [FileZilla](http://filezilla-project.org/)
2. Enter the following connection parameters: 
	* host: orchestra.med.harvard.edu
	* port: 22 (SCP/SFTP port)
	* username
	* password

	
For additional help, see the [Orchestra Wiki](https://wiki.med.harvard.edu/Orchestra/NewUserGuide)

## xQuartz
System for visualizing graphics while working in terminal.
[Download xQuartz for Mac](https://www.xquartz.org/)

To enable X11 forwarding for 1 session: 

	ssh -X username@orchestra.med.harvard.edu
	
To enable X11 forward by default, add the following to the `~/.ssh/config` file: 

	Host orchestra.med.harvard.edu
	ForwardX11 Yes
	


*X11 is disabled by default in SSH clients because the remote hosts can view your X11 server*

