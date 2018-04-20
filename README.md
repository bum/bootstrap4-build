The bootstrap 4.1 download from https://github.com/twbs/bootstrap/tree/v4.1.0 includes too many files/folders that we do not need: \_data, \_includes, \_layouts, assests, dist, docs, nuget... 

We just keep 
* folder "**js/src**" (remove js/dist, js/tests) 
* folder "**scss**"
* **build/rollup.config.js** & **build/postcss.config.js**
* **package.json** find and remove all scripts name includes "docs", "lint", "test"... and remove all useless (for us) dependencies, change "**index.js**" to "**index-app.js**" and "**bootstrap.scss**" to "**bootstrap-app.scss**" and config the generated js to outside of the "js" folder, moving all to "dist" folder.
* **.babelrc.js**

You can download the final from this git. As they release new version, just copy 2 folders "js/src" & "sass", of course in case they do not change the build process.

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
