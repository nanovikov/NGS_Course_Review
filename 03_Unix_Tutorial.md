#Unix

## Shortcuts

* "control+c" will cancel the command you are writing, and give you a fresh prompt.
* "control+a" will bring you to the start of the command you are writing.
* "control+e" will bring you to the end of the command


## Filesystems

To see where you are: 

	pwd
	
To go up a level: 

	cd ..
	
To stay in the same directory: 

	cd .
	
To go to the home directory: 

	cd ~

To make a new directory:

	mkdir path-to-directory
	
To copy a directory with all of its contents:

	cp -r path-to-directory path-to-new-location
	
To move to a directory:

	cd path-to-directory
	
To see what is in the directory in a nice format:

	ls -lthFr


## Less

* "spacebar" : to go forward
* "b" : to go backward
* "g" : to go to the beginning
* "G" : to go to the end
* "q" : to quit
* "/" : to search

## Head

To view a specific number of lines use option `-n`: 

	head -n 1 file-name

## Alias

To make an alias for a command add the following line to ~/.bashrc:

	alias new_command_name='list_of_commands'

Then do: 

	source ~/.bashrc

## Exercises
	
### Exercise 1

Set up your `ngs_course` directory: 

	cd ~
	mkdir ngs_course
	cp -r /groups/hbctraining/ngs-data-analysisSummer2016/unix_lesson/ ngs_course


List the `Mov10_oe_1.subset.fq` files from your home directory. (Hint: The file is located in ngs_course > unix_lesson > raw_fastq)

	ls -lthFr ngs_course_rep/unix_lesson/raw_fastq/Mov10*1*
	
### Exercise 2

Change directories to `/home/username/ngs_course/unix_lesson/raw_fastq/`, and list the contents of `unix_lesson/genomics_data` without changing directories again.
	
	ls -lthFr ../genomics_data/
	
List the contents of the `/bin` directory. Do you see anything familiar in there? How can you tell these are programs rather than plain files?

	ls -lthFr /bin

*The `-F` option for command `ls` adds a special character to specify filetype. Command names are followed by an `*`*
	
### Exercise 3
Do each of the following using a single `ls` command without navigating to a different directory.

1. List all of the files in `/bin` that start with the letter 'c'

		ls -lthFr /bin/c*

2. List all of the files in `/bin` that contain the letter 'a'

		ls -lthFr /bin/*a*

3. List all of the files in `/bin` that end with the letter 'o'

		ls -lthFr /bin/*o
		
4. List all of the files in `/bin` that contain the letter 'a' or 'c'.

		ls -lthFr /bin/*a* /bin/*c*

### Exercise 4

Find the line number in your history for the last exercise (listing files in `/bin`) and reissue that command.		

	history
	!1021

### Exercise 5

1. Create a new directory called `backup_ref_data` in `~/ngs_course/unix_lesson/` 

		mkdir ~/ngs_course_rep/unix_lesson/backup_ref_data

2. Copy over the contents of the `~/ngs_course/unix_lesson/reference_data/` into `backup_ref_data` after changing directories to `~/ngs_course/unix_lesson/` (if you are not already there).

		cp ~/ngs_course_rep/unix_lesson/reference_data/* ~/ngs_course_rep/unix_lesson/backup_ref_data/

3. Using just one command, move the `raw_fastq/backup/` directory to your current working directory (which is `~/ngs_course/unix_lesson/`) and rename it `backup_fastq`.

		mkdir ~/ngs_course_rep/unix_lesson/raw_fastq/backup
		mv ~/ngs_course_rep/unix_lesson/raw_fastq/Mov10_oe_1.subset.fq backup/Mov10_oe_1.subset-copy.fq
		mv ~/ngs_course_rep/unix_lesson/raw_fastq/backup/ ~/ngs_course_rep/unix_lesson/backup_fastq/

4. Remove backup directories carefully

		rm -ri backup_ref_data/ backup_fastq/ 
		

For more commands, look [here](https://github.com/swcarpentry/DEPRECATED-boot-camps/blob/master/shell/shell_cheatsheet.md).

This material has been adapted from a lesson developed by members of the teaching team at the [Harvard Chan Bioinformatics Core](http://tinyurl.com/hbc-ngscourse-page) (HBC). These are open access materials distributed under the terms of the [Creative Commons Attribution license (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/), which permits unrestricted use, distribution, and reproduction in any medium, provided the original author and source are credited.

The materials used in this lesson were derived from work that is Copyright © Data Carpentry (<http://datacarpentry.org/>). All Data Carpentry instructional material is made available under the [Creative Commons Attribution license (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).
Adapted from the lesson by Tracy Teal. Original contributors: Paul Wilson, Milad Fatenejad, Sasha Wood and Radhika Khetani for Software Carpentry (<http://software-carpentry.org/>)
	
	





