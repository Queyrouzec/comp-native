# comp-native
Natively compiled web apps without js, html, and css in mind.

There are a lot of cross platform frameworks, but when it comes to low level high performance javascript free code
there are no good options.

## The goals of this framework are as follows

### 1) Make a framework that can work purely in Zig

It should be noted that comptime is code that you can write alongside your normal code that must have a final result when your code is compiled.
It can and usually takes advantage of types but it's benifits are not limited to typesetting. It is macros written like a normal program.

Zig has several benifits:

1. Comptime in build files. Comptime variables and build files make it easy for users who don't have experiance with manual memory management
to customize the default setting on high level abstractions of the framework.
2. Comptime for cross platform clarity.
3. Simple to understand and easy to write.
4. Fast comptimes. This is extremely important for UI. TODO: Will talk about this more later. Add link.
5. Easy interop with C. All my homies want this.
6. The language needs to be low level to enable maximum performance.
7. Only compiles what's needed.

Pure Zig is more of an ideal than a reality, but there will be an attempt.

Having something that is purely Zig will allow for easier use of higher levels of abstraction and low level customization.

### 2) Have no opinions

Opinions are assumptions that limit what you can do you and in most cases must be learned in order to properly implement. If you're going to go
down this route, I'd rather give you the option of having minimal chosen opinions through build files.

### 3) Allow for imported opinions through build.zig and comptime

I hope that there will be a rich eco system of 3rd party, proper, easy to implement opinions for your usecase where you can atlease have
accurate assuptions.

There will be a few basic defaults to choose from

### 4) Be an inch deep and a mile wide

I'd rather have 4 function calls than 20 for reusability. Functions sometimes must have and hide certain assumptions and the less assumptions
there are the better off the code base is. Excessive functions can also clog up namespaces and make code harder to read and understand.

This is, however, a trade off. Reused code has the benifit of being well tested by it's own useage. It also has the advantage of giving
more control to the dev when choosing size vs speed.

We should lean towards less functions, but it will always be a trade off on a case by case basis.

### 5) Tools to easily access the framework through higher level languages

Proper c interop can allow this framework to utalize a host of different languages for different use cases.

In my experiance, it doesn't matter how many frameworks you have. If your language is not suited for the task it's given then the only thing you
can and should do is embrace the suck.

Goals for c interop:
1. There should be a path for automatic documentation generation in the higher level language.
2. You should want to set defaults in Zig.
3. Zig (hopefully) should be your only dependancy besides the higher level language.
4. There must be only one command for building your Zig binaries upon creating any new project.
5. It should be easy to turn off and on assertions, production, and dev builds in Zig.
6. It should be easy to add your own Zig code.

## Roc Lang

Roc is the high level language that we want to use for "official" support.
- It's aiming to be as fast as Go in both speed and compilation.
- It natively allows for hot reload and code push.
- It's being built for the server so you can use this for both frontend and backend.
- It's quick and easy to write.
- It's immutable by default which is a feature in pretty much every frontend statemanagement library.

Since Roc is very new, this is very subject to change; but if it works, I believe it can create advantages that no other non-js framework can compete with.
