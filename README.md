## Why do I want to reinvent the browser?

It's just a fun little experiment. I don't know for how long exactly, but for decades, the way our web browsers work has remained unchanged. There's a renderer that displays your HTML and coupled to it is a Javscript engine that lets you add interactivity, data processing, page manipulation and etc to your website through scripts.

This can be a little restrictive in the ways you can express your applications but we've come up with creative ways of getting around this by building frameworks and libraries. You can build your apps the way you want them, in the language you choose and in the paradigms of your liking. But they all still compile down to the same HTML, CSS and Javascript. So you're restricted by the capabilities of these fundamental components. Now browsers have gotten better and better at processing these languagse like Chrome's' V8 engine and now with the introduction of WebAssembly, which so fast that you can build 3D games for the browser.

But if you still feel like your app is restricted by this, you will probably decide to build a desktop or mobile app for your audience. Build it in native and make it blazing fast and snappy with all of the RAM and compute of the device at your disposable. But now you have to sit and worrying about distribution. Your user has to download and install your app on their device. This is easy for a website, all the user has to do is enter a URL into the browser and they're on the app. No install wizard, no running the application, no fuss. They're just on the app right away. Ofcourse with a webapp you can't persist data on the device but in this day and age no application is really storing data on device other than for caching purpose. It's all on the cloud anyway.

So you have two options:
 - You build a website and work within the confines of a browser
 - You build native apps and figure out distribution

The real issue here is that the browser forces you to use HTML, CSS, Javscript and WASM.

## Why can't we just ship a binary to the user?

Well the issue that surfaces here is security, binaries can do as they please on the device, read from disk, write from disk and there's no assurance that communications in the binary are done securely over HTTPS like in the normal browser. The webbrowser provides a secure environment for your webapp to run and ensures the user that it does not meddle with your system and does not leak information to listeners on the web.

## How do we provide a secure environment to run binaries?

Well if you think about it, this technology already exists in the world of web, just not in your browser. Containerization is becoming more and more popular as a way to package and deploy your servers on the cloud, where you don't control the underlying system and also protect other servers from any malicious intent you may have on the cloud. So the same security measures that the browser provides can easily be achieved with container technology. We can control the environment and resources a container has access to and even control the communication channels. Restricting access to file system is one of the most basic features in a system like Docker.

### But how do you prevent unsecure communication to servers?
Well you remove networking capabilities from the container and instead give an abstracted way to establish only HTTPS connections.

### But container applications don't have GUIs.
That's because the applications we've been running in containers don't need GUIs. They're usually webservers and things that run in the backrground of your system. It's easy to build a secure bridge to the container to allow it to draw directly on the browser window.

## How do I plan on achieving this?

Well as a proof-of-concept, I will first need to build a very minimal GUI interface that act as your browser and the I will need to build a bridge to the container to draw on that window. I wil probably use C++ and Docker for this but we'll just have to see.

This repository will also act as the repo for this project.