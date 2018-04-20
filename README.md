After download bootstrap 4 source, we run install

``
$ npm install 
``

and get "python" error and stuck from this. The reason is that: bootstrap use **note-sass** to compile sass files, 
*on windows* this package require *node-gyp* prerequisites. 

https://github.com/nodejs/node-gyp#on-windows

We have to install **windows-build-tools** from CMD/PowerShell **running as Administrator**

``
$ npm install --global --production windows-build-tools
``

This will automatically install 
[[`Visual C++ Build Tools`](http://landinghub.visualstudio.com/visual-cpp-build-tools)]
and Python 2.7 (**exactly version 2.7**, v3.x.x is not supported)
[[`Python version 2.7`](https://www.python.org/downloads/)]
. The installation takes place about 10 minutes or more. After finished, you can find Python 2.7 installed in folder
C:\Users\\*USER-NAME*\\.windows-build-tools\python27

That's fine, now take back to the working space, set evn "python" to the file "**python.exe**"

``
$ npm config set python C:\Users\\*USER-NAME*\\.windows-build-tools\python27\python.exe
``

Now you can start "npm install" and get the results.
