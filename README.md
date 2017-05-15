
Just some quick code to check if OpenCL stuff compiles, links and runs correctly (like, for testing OpenCL inside a VM).

I figured I just need this:

	apt-get install ocl-icd-opencl-dev

If you wanna see more stuff:

	apt-cache search opencl | grep opencl

Compile it:

	gcc -o main.exe main.c $(pkg-config --libs --cflags OpenCL)

Or simply:

	gcc -o main.exe main.c -lOpenCL 

Output will be like:

	main.c: In function ‘main’:
	main.c:55:1: warning: ‘clCreateCommandQueue’ is deprecated [-Wdeprecated-declarations]
	 command_queue = clCreateCommandQueue(context, device_id, 0, &ret);
	 ^
	In file included from main.c:7:0:
	/usr/include/CL/cl.h:1359:1: note: declared here
	 clCreateCommandQueue(cl_context                     /* context */,
	 ^
	main.c:76:1: warning: ‘clEnqueueTask’ is deprecated [-Wdeprecated-declarations]
	 ret = clEnqueueTask(command_queue, kernel, 0, NULL,NULL);
	 ^
	In file included from main.c:7:0:
	/usr/include/CL/cl.h:1373:1: note: declared here
	 clEnqueueTask(cl_command_queue  /* command_queue */,


(yea, who gives a fuck)

Output be like in VMWare on Windows 10, running Xubuntu 16.06.2 as guest:

	line 45 ret = -1001
	line 48 ret = -32
	line 67 ret = -44 (clBuildProgram)
	line 74 ret = -48
	line 77 ret = -36
	line 81 ret = -36
	��

CBA for enum2string functions.

