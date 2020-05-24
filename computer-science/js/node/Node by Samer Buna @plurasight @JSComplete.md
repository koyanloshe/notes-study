# Node by Samer Buna @plurasight @JSComplete

TODO

**_Practical example : Task List Manager - not understood.._**
**_Console & utilities - need to watch utils again_**
**_Debugging NodeJS Applications - need to watch debugger action again_**

## Node Architecture and how it is different from Javascript

**_### The CLI
_****### 

**
The CLI/REPL has interesting options such as .help which opens up useful features like 
.editor which allows multi-line code 
.save which saves REPL code to a designated file
And so on.

_### Process & Buffer
_### 

`process.env `
can be set but should not be source for a getter so instead of 
`process.env.port`

it is better to have a config.json from which u retrieve port 
`{`
`	port: process.env.port || 8080,`
`}`

Buffer operations are written to the same memory address. Eg. slicing a buffer slices the buffer itself and does not return a new sliced buffer. So use carefully.

String decoder is needed to interpret UTF8 formatted content. 

`Buffer.toString()`
fails to interpret UTF8 and throws a ? Symbol when it fails

**_### Understanding Require
_****### 

**
Resolving > Loading > Wrapping > Evaluating > Caching

Node first looks for the required module in module.paths 
Core Node modules are an exception to this search method.

`Require.resolve() `
helps locate a file

Export cannot be used inside timers as the state of loaded set by Node in module.loaded changes based on timing of the statement evaluation.

**_### JSON and C++ files
_**
Require will try .js then .json then .node files
.node is a compiled add-on module.

Create a addon directory and add the cc file there.
Then add a binding.gyp file and add below config
`{`
`	“targets”: [`
`		{`
`			“target-name”: addon“,`
`			“sources”: [“file1.cc”]`
`		}`
`	]`
`}`

From within the addon folder run 
`node-gyp configure `

ensure node-gyp is globally installed using 
`npm i -g node-gyp`

This process creates a build directory and build files
Then run 
`node-gyp build `
and that creates the addon.node file which can be included  in the app using require

**_### Evaluating required files
_****### 

**
When a file is required by Node, it follows the sequence mentioned in 
`require(‘module’).wrapper`

This is
`[function(exports, require, module, __filename, __dirname)]`

this can be seen by typing require(‘module’).wrapper in REPL

To check if a script is running via command line or from within a file, 

`if(require.main == module){`
`	// Running as a script via REPL`
`	// accept process.argv arguments. `
`} else {`
`	// Being required from within a file`
`}`

_### Caching of files
_
require.cache shows the cached path of the file. 
`delete require.cache[filename]`
Allows to delete the cache.

Alternatively execute require(‘module’) as a function such as
`require(‘module’)()`
to repeatedly require the same file’s contents.

## NPM

Npm registry can be used with git repositories 
`npm i expressjs/express`
this will install express from GitHub

`npm i -—dry-run`
Will allow to see package contents without installation

`npm ls -g —-depth=0`
To see the installed packages

`npm ll -g —depth-0`
shows more description about installed packages.

`npm ls -g —-depth=0 -—json`
to get the output in json format instead of as a shell return.

`npm config set init-author-name “Alok Shenoy”`
to set the default value of author name for init 

`npm config list -l | grep init`
`npm home lodash`
Allows home page of a package

`npm repo lodash`
Shows repo page of package

`npm prune `
Removes dependencies that were temporarily installed

`npm xmas`
`npm visnup `
For tp

## Concurrency Model & Event Loop

NodeJS libuv == Ruby Event Machine == Python Twisted

IO in node context is when disk and network operations are performed.
Slow IO can be processed 
* synchronously, 
* fork(), 
* threading (Apache is multi-threaded, nginx is single-threaded), 
* event loop

### Event Loop

A loop that picks events from the event queue and pushes their callback to the call stack

V8 has a heap and stack. Event loop depends on the libuv library.

The v8 call stack is pop-in pop-out - on LIFO basis
![Node by Samer Buna @plurasight @JSComplete-1](images/Node%20by%20Samer%20Buna%20@plurasight%20@JSComplete-1.png)

Blocking code can be written in Node. Prevention is key.
When call stack gets empty:
While the queue is not empty:
	Event = dequeue an event
	If there is a callback:
		Call the event’s callback.

### setImmediate & process.nextTick

![Node by Samer Buna @plurasight @JSComplete-2](../../../assets/images/Node%20by%20Samer%20Buna%20@plurasight%20@JSComplete-2.png)

SetImmediate triggers even before zeroth second.
Process.nextTick is after executing process completes.

First case is where the fileName validation is synchronous.
![Node by Samer Buna @plurasight @JSComplete-3](../../../assets/images/Node%20by%20Samer%20Buna%20@plurasight%20@JSComplete-3.png)

So if we change the fileName to a number, the console.log(“Hello”) does not execute. This is blocking IO
![Node by Samer Buna @plurasight @JSComplete-4](../../../assets/images/Node%20by%20Samer%20Buna%20@plurasight%20@JSComplete-4.png)

However, if we wrap the validation with a process.nextTick, then the first pass prints the Hello message and the nextTick handles the fileSize function execution.
![Node by Samer Buna @plurasight @JSComplete-5](../../../assets/images/Node%20by%20Samer%20Buna%20@plurasight%20@JSComplete-5.png)

Understanding setImmediate, setTimeout and process.nextTick is key to understanding the event loop

## Async - event-driven

Callbacks != Async

Using promises and callback interfaces in the same code

![Node by Samer Buna @plurasight @JSComplete-6](../../../assets/images/Node%20by%20Samer%20Buna%20@plurasight%20@JSComplete-6.png)

`cb = () => {} `
Sets a default value for callback

Lines 8 & 13 are for the callback interface to work
Lines 4, 7, 12 are for the Promises interface to work.

This code will work with promises AND callbacks.

**_The pattern used in attendance-system is ideal as per Samer Buna too_**
**_
_**
**_### Event Emitter
_**
It is synchronous code
 
If you use uncaughtException
`process.on(‘uncaughtException’, (err)=>{ 	console.log(err);`

`	// do whatever cleanup`

`	process.exit(1) })`

UncaughtException process listening prevents node from exiting process.

.prependListener helps move a listener up in the sequence of execution**_
_**
**_
_**
**_Net, UDP & DNS modules_**
**`net.createServer() `****_
_**
creates an event emitter

Dgram stands for UDP Datagram
`dgram.createServer()`
Also creates an event emitter

DNS depends on libuv and needs the event loop.

## Node for Web

The structure of URL to be parse and understanding query strings
![Node by Samer Buna @plurasight @JSComplete-7](../../../assets/images/Node%20by%20Samer%20Buna%20@plurasight%20@JSComplete-7.png)

`const server = http.createServer()`
Is an instance of Server Class and is an EventEmitter

`http.get() `
Is of type ClientRequest

`server.on(‘request’, (req, res)=>{`
`	// req is an instance of IncomingMessage Class`
`	// res is an instance of ServerResponse class`
`})`

List all status codes by using http.STATUS_CODES
List all methods by using http.METHODS

Using REPL helps get realtime interpretation of requests

## Streams

![Node by Samer Buna @plurasight @JSComplete-8](../../../assets/images/Node%20by%20Samer%20Buna%20@plurasight%20@JSComplete-8.png)

Readable streams start in pause mode and then go to flowing mode..
Stream.read() is pause mode
EventEmitter is in flowing mode
Stream.resume() and Stream.pause() are used to switch between pause and flow

## Clusters and Child Processes

Cloning, Decomposing, Splitting are various scalability strategies.

Child processes can be created using 
`spawn() || fork() || execFile() || exec()`

Spawn creates a child process instance. It does not create a shell. It is more efficient
Exec uses a shell. It buffers the output.
You can force shell true in spawn.
execFile is exactly like exec but doesn’t use shell so is slightly more efficient than exec but less efficient than spawn.

Load testing using apache benchmark
`ab -c200 -t10 http://localhost:8080/`

Cluster can help to improve performance by 3x at least

