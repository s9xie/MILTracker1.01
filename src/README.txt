UPGRADE the MILTRACKER 1.0 ORIGINALLY BY Boris Babenko.
MILTRACKER 1.0 relies on IPP 6.0 and opencv 1.0.1 which are quite outdated. 
This release MILTRACKER 1.0.1 made several changes in the source code to make it compatible with the lastest opencv (2.4.7) and IPP (8.0).
To use the code and run the demo, please follow the instructions below
**(Tested on Windows 7 64-bit, and Compile the source code in Win32 Debug mode)

1. Install IPP 8.0 here:
https://registrationcenter.intel.com/RegCenter/AutoGen.aspx?ProductID=1943&AccountID=&EmailID=&ProgramID=&RequestDt=&rm=EVAL&lang=&pass=yes
This link provides a 30-days free trial. Ask me for a activation file in person if needed.

*The default path should be like "C:\Program Files (x86)\Intel\Composer XE\"
*You may need to also install Intel Composer XE if you haven't yet.

2. Install OpenCV.
The instructions below is suitable for opencv 2.4.7. However, it should work for all versions of opencv after opencv 2.1 with minor changes in 
the environment setting.

3. Setting system path:
Environment Variables -> System variables -> Path:

C:\opencv\build\x86\vc11\bin; 
C:\Program Files (x86)\Intel\Composer XE\ipp\bin\ia32\;
C:\Program Files (x86)\Intel\Composer XE\redist\ia32\ipp;


3.Open the .sln project file of MILTracker. 
 
Project->Properties->Configuration Properties->C/C++->General->Additional Include Directories:
C:\Program Files (x86)\Intel\Composer XE\ipp\include
C:\opencv\build\include\
C:\opencv\build\include\opencv

Project->Properties->Configuration Properties->Linker->General->Additional Library Directories

C:\opencv\build\x86\vc11\bin;
C:\opencv\build\x86\vc11\lib;
C:\Program Files (x86)\Intel\Composer XE\compiler\lib\ia32;
C:\Program Files (x86)\Intel\Composer XE\ipp\lib\ia32;
C:\Program Files (x86)\Intel\Composer XE\redist\ia32\ipp;

Project->Properties->Configuration Properties->Linker->Input

opencv_calib3d247.lib
opencv_calib3d247d.lib
opencv_contrib247.lib
opencv_contrib247d.lib
opencv_core247.lib
opencv_core247d.lib
opencv_features2d247.lib
opencv_features2d247d.lib
opencv_flann247.lib
opencv_flann247d.lib
opencv_gpu247.lib
opencv_gpu247d.lib
opencv_highgui247.lib
opencv_highgui247d.lib
opencv_imgproc247.lib
opencv_imgproc247d.lib
opencv_legacy247.lib
opencv_legacy247d.lib
opencv_ml247.lib
opencv_ml247d.lib
opencv_nonfree247.lib
opencv_nonfree247d.lib
opencv_objdetect247.lib
opencv_objdetect247d.lib
opencv_ocl247.lib
opencv_ocl247d.lib
opencv_photo247.lib
opencv_photo247d.lib
opencv_stitching247.lib
opencv_stitching247d.lib
opencv_superres247.lib
opencv_superres247d.lib
opencv_ts247.lib
opencv_ts247d.lib
opencv_video247.lib
opencv_video247d.lib
opencv_videostab247.lib
opencv_videostab247d.lib
ippi.lib
ippm.lib
ippcore.lib
ippcv.lib
ipps.lib



Once this is done you should be able to compile the code. If it fails with an error message "libiconv-2.dll" missing, use the dll file in the demo folder and put it in the same folder as where the complied .exe file is.