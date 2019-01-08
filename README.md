1) About:

This is a multi-threaded web server using POSIX threads in C to showcase thread programming and synchronization methods knowledge. The web server should be able to handle any file type: HTML, GIF, JPEG, TXT, etc. and of any arbitrary size. It should handle a
limited portion of the HTTP web protocol (namely, the GET command to fetch a web page / files).

2) How to compile:

A makefile was provided in the tar submission. The makefile was altered to compile the code with -g option so that debugging could be achieved using valgrind. 
	
	make

3) How to run:

After unzipping the project folder, use make to produce an executable. Then use the following command to run the program.

	./web_server <port> <path> <num_dispatcher> <num_workers> <dynamic_flag> <queue_length> <cache_entries>

	<port> - the port you wish to access the web server from

	<path> - path to root of web server

	<num_dispatcher> - the number of dispatcher threads to create (max 100)

	<num_workers> - number of worker threads to create (max 100)	

	<dynamic_flag> - Always 0

	<queue_length> - The length of the request queue

	<cache_entries> - The number of files to cache

In another terminal window, run a command that will produce a request to the server using wget for instance. 

To terminate the program, hit ^C in the terminal window where the server is running.

4) Caching Mechanism

LFU - Least Frequently Used. When new items are added to the cache, they are initialized with a frequency of 0. Then every time a request comes in for a particular cache entry, that entry's frequency is incremented by one. Then when a new item needs to get added to a full cache, the entry with the lowest frequency (first in cache if tie) is replaced

5) Web Server Logging:

The logging mechanism creates a new file in the web tree root directory named "web\_server\_log" if it does not already exist from a previous run of the program. The server will append all of its request logging to the end of the "web\_server\_log" file, i.e. it will not overwrite the contents of the previous run. 
   


