MILTRACK README, Version 1.0
-------------------------------------------------------------------------------------------------------

This code includes an implementation of the MilTrack algorithm [1], as well as a re-implemenation of the Online AdaBoost tracker described in [2], though with some modifications.  This code requires both OpenCV 1.0 (http://sourceforge.net/projects/opencvlibrary/) and Intel IPP 6.0 (http://www.intel.com/cd/software/products/asmo-na/eng/302910.htm) to be installed on your machine.  It has only been tested on a machine running Windows XP, usiong Visual Studio 9.0.  In order for the code to run, make sure you have the OpenCV bin directory, and the Intel IPP bin directory in your system path.

IMPORTANT NOTE: The current version of OpenCV (1.0.1) contains a bug which will cause the video outputs of my code to produce garbage.  If the only output you desire is the (x,y) locations of the object, then there should be no problems.  Otherwise, if you want to save output videos (with a colored box around the target etc) you will need to download a patch to fix the problem, or wait for OpenCV to release a fixed version.  Please see http://n2.nabble.com/Re%3A-cvCreateVideoWriter-problem---Windows-Vista-tc2217642.html#none for more info.  That patch can be downloaded from the yahoo group (the file is ffopencv110.rar - it contains a fixed dll).

Copyright 2009 Boris Babenko (bbabenko@cs.ucsd.edu | http://vision.ucsd.edu/~bbabenko).  Distributed under the terms of the GNU Lesser General Public License (see the included gpl.txt and lgpl.txt files).  Use at own risk.  Please send me your feedback/suggestions/bugs.

Project Website: http://vision.ucsd.edu/~bbabenko/project_miltrack.shtml

References:
	
[1]  	Visual Tracking with Online Multiple Instance Learning
	B. Babenko, M.H. Yang, S. Belongie
	CVPR 2009

[2] 	On-line Boosting and vision
	H. Grabner and H. Bischof
	CVPR 2006

-------------------------------------------------------------------------------------------------------
RUNNING FACE TRACKER DEMO

Included in the zip file is an executable called MilTrack-Face.exe (in the release directory).  This demo uses the built in OpenCV face detector to initialize the tracker.  Note that this executable uses the included xml file, and has to be run from the same directory as that xml file (the xml file includes the classifier that's used by OpenCV for face detection).  You can pass in a single command line argument specifying a file to which a video will be saved.  If no arguments are passed in, the output will not be saved.


USAGE:

> MilTrack-Face.exe [optional filename]

-------------------------------------------------------------------------------------------------------
RUNNING MILTRACK ON PRE-RECORDED VIDEO

To run the tracker on a pre-recorded video you must follow the following conventions (you can easily change these by editing the code).  The code takes an image sequence as input (again, you can easily use video input if you edit the code).  Suppose your clip is called VidClip1.  You must set up a directory with the following contents:

	VidClip1/imgs - this sub-directory should contain the images of the video clip; they should be names img00000.png, img00001.png, etc

	VidClip1/VidClip1_frames.txt - this should be a text file with one line; that line should contain the start and end frames of the sequence, comma seperated.  E.g. "0,100" would indicate that the video ranges from img00000.png to img00100.png.

	VidClip1/VidClip1_gt.txt - this is the ground truth file;  every line in this file corresponds to a frame of the sequence, and contains the [x,y,width,height] information.  At minimum this file should contain 1 line indicating the initial location of the object.

Of course you can substitute "VidClip1" with a name of your choice.  See the examples of data provided on the website.


USAGE:

> MilTrack.exe [parent directory] [name] [default=1 | alg switch, 1=MilTrack 2=OAB1 3=OAB5, see paper for details] [default=1 | trial number] [default=0 | save video output 0/1]

The first parameter is the parent directory, and name is "VidClip1" in the above example.  Note -- the executable is in the release directory.

-------------------------------------------------------------------------------------------------------
COMPILING CODE

The zip file includes a MS Visual Studio 9.0 Solution file (.sln).  You should be able to open this file in MS Visual Studio 2008/9.0.  You will have to set up the Project Properties so that the project has access to the OpenCV and IPP header files (note, to run the code, the bin directories for both OpenCV and IPP must be included in your path).  The following properties need to be modified appropriately:

Project->Properties->Configuration Properties->C/C++->General->Additional Include Directories
Project->Properties->Configuration Properties->Linker->General->Additional Library Directories

Once this is done you should be able to compile the code.
