jData Interface Library (JIL) is a refrence implementation of an interface library to jData. The current release version of JIL is 0.0.4. As of version 0.0.4 all methods are chainable and the main JIL function returns itself if `JIL[arguments[0]]` is not a function. For example, `JIL.remove("fullname").set("status", "Editing page on EliGrey.com")` is the equivalent of `JIL.remove("fullname"); JIL.set("status", "Editing page on EliGrey.com")` **Please note:** All JIL methods are asynchronous, so don't expect `JIL.set("foo", "bar").get("foo", print)` to print always print "bar". JIL has the following fields and methods: **Methods: **addEvent, get, requestCallbacks.reset, handleResponse, total, list, loadFrame, query, remove, removeEvent, set, trust, untrust **Fields: **frame, frameActive, origin, path, ready, requestCallbacks 
## Demo You can see JIL in action at the 

[demo page][1]. 
## Methods

*   JIL([arguments]) - Usage: JIL([prop [, arg1 [, ect]]]); The JIL function either returns itself or a property specified in the first argument if there is only one argument. 
    *   `JIL("get", "OpenID", console.log)` is the same as `JIL.get("OpenID", console.log)` and returns JIL
    *   `JIL("trust")` will run `JIL.trust()` and returns JIL
    *   `JIL("origin")` will return `JIL.origin`
    *   `JIL("undefined property that doesn't exit")` returns `JIL`
*   JIL.get(item:String [, callback]) - Gets value of an item. Callback is passed the value or null if item is not defined.
*   JIL.set(item:String, value:String [, callback]) - Sets value of an item. Callback is passed true if it was successful and false if it was unsuccessful.
*   JIL.requestCallbacks.reset([key]) - Deletes JIL.requestCallbacks[key] or just resets JIL.requestCallbacks to only have this method. Returns the JIL object.
*   JIL.remove(item:String [, callback]) - Removes an item. Callback is passed true if it was successful and false if it was unsuccessful.
*   JIL.list([callback]) - Lists every item. Callback is passed an array with the name of each item.
*   JIL.total([callback]) - Gets amount of items. Callback is sent an integer representing the amount of items.
*   JIL.trust([callback]) - Request to become trusted host. Callback is passed true if it was successful and false if it was unsuccessful.
*   JIL.untrust([callback]) - Request to become an untrusted host. Callback is always passed true.
*   JIL.loadFrame([readyCallback]) - Append JIL.frame to the <head> tag (IE8 has problems with document.documentElement); can be called more than once to change jData hosts. readyCallback is passed the JIL object once the frame has loaded.
*   JIL.addEvent(obj, type:String, fn:Function) - Adds an event listener that runs the function, fn, for the event type.
*   JIL.removeEvent(obj, type:String, fn:Function) - Removes an event listener that runs the function, fn, for the event type.
*   JIL.handleResponse(event:MessageEvent) - Used internally by JIL to handle responses sent from the jData host.
*   JIL.query(obj [, callback]) - Used internally by JIL for all of the request functions to send a JSON-encoded object to JIL.frame. Field Explanations: 

*   JIL.orgin:String - The jData website to load without a pathname (this will be the variable to use when checking message origins)
*   JIL.path:String - An optional path in case the jData host is in a subdirectory, otherwise leave it as an empty string
*   JIL.frame:HTMLIFrameElement - The frame used for communication between the client and jData host.
*   JIL.frameActive:boolean - Boolean representing if the frame has been appended to the document.
*   JIL.ready:boolean - Boolean representing if JIL is able to send messages to JIL.frame (JIL.frame has loaded).
*   JIL.requestCallbacks:Object - Used internally to store references to callbacks associated message ID until the message is responded to, at which point the callback is ran then deleted.
*   JIL.listening:boolean - Boolean representing if JIL.handleMessage is listening for message events yet.

 [1]: http://code.eligrey.com/jdata/jil/demo.html
