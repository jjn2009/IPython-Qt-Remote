IPythonQtRemote
=============

This is a simple set of bash scripts meant to make your life easier with ipython qtconsole using a remote kernel

Assumptions:
* The _client_ is OS X
* The _server_ is linux or unix
* /tmp/ exists and accessible on the server and client
* _IPython QT_ is set up correctly on the client
* _IPython_ is set up correctly on the server
* SSH keys are set up correctly

Instructions:
* clone the directory
* edit /IPythonQtRemote.app/Contents/MacOS/IPythonQtRemote to point to the correct ssh server
* put _IPythonQtRemote.app_ wherever you please
	* "/Applications/"
	* "/Users/YOUR_USERNAME/Applications/"
* place "create-ipy" in some directory that exists in your PATH environment variable on the server
* launch _IPythonQtRemote_ through finder.
* optionally anchor it to the dock by right clicking the icon after you have launched it

Why?
* I have an intel atom box with a Nvidia 750ti which I want to do basic CUDA programming on and what better way than to put a nice icon in my dock to get up and running with ease

Known Issues:
* JSON files are going to pile up in ~/.ipython/profile_default/security/ (a few hundered bytes each)
	* There may be some adverse implications due to PID collisions if you are launching lots of kernels and not regularly cleaning that directory out.
* No control over which kernel you connect to. 
	* If a kernel exists then you connect to the one with the lowest pid (likely oldest, but pids are recycled so not always)
	* A new kernel is launched if none are found to be running and connected to

Notes:
* when close the window on your qtconsole the kernel continues to run on the server
* typing exit in the console kills your kernel on the server
