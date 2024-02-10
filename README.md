# comp-native
Natively compiled web apps without js, html, and css in mind.

There are a lot of cross platform frameworks, but when it comes to low level high performance javascript free code
there are no good options.

## Note on comptime for those who haven't used Zig

It should be noted that comptime is code that you can write alongside your normal code as long as it can be run and resolved when the program is compiled.
It can and usually takes advantage of types, but it's benifits are not limited to typesetting. It is macros written as normal code.

This is a function that takes a unsigned number and turns it into bytes. You give the function a number type, `size`, of u16, u32, or u64 and it returns an u8 array
with 2 (`[2]u8`), 4 (`[4]u8`), or 8 (`[8]u8`) elements respectively.

![image](https://github.com/Queyrouzec/comp-native/assets/45217520/965d0b64-db21-466b-80ed-bae9c857559f)

This one function gets compiled into three functions and each one is called based on the type you give it.

Comptime cannot use manual memory allocation due to it's deterministic requirements.

## The goals of this framework are as follows

### 1) Make a framework that can work purely in Zig

Zig has several benifits:

1. Comptime in build files. Comptime variables and build files make it easy for users who don't have experiance with manual memory management
to customize the default setting on high level abstractions of the framework.
2. Comptime creates cross platform clarity.
3. Simple to understand and easy to write.
4. Fast compilation times. This is extremely important for UI. TODO: Will talk about this more later. Add link.
5. Easy interop with C.
6. The language needs to be low level to enable it's nieche for high level app performance.
7. Only compiles what's needed. (tree shaking)

Pure Zig is more of an ideal than a reality, but there will be an attempt.

Having something that is purely Zig will allow for easier use of higher levels of abstraction and low level customization.

### 2) Have no opinions

Opinions are assumptions that limit what you can do you and in most cases must be learned in order to properly implement. If you're going to go
down this route, I'd rather give you the option of choosing the opinions you abide by through build files.

### 3) Allow for imported opinions through build.zig and comptime

I hope that there will be a rich eco system of 3rd party, usecase specific, easy to implement opinions for you where you can make better assuptions.

There will be a few basic defaults to choose from.

### 4) Be an inch deep and a mile wide

I'd rather have 4 function calls than 20 for reusability. Functions sometimes must have and hide nessisary assumptions, and the less assumptions
there are the better off the code base is. Excessive functions can also clog up namespaces and make code harder to read and understand. However,
this is a trade off. Reused code has the benifit of being well tested by multiple use cases and faster to implement. It also has the advantage
of giving more control to the dev when choosing size vs speed.

We should lean towards less functions, but the decision will always be on a case by case basis.

### 5) If it fails, fail quick and hard

For a framework, it is better for the app dev to expect a crash than it is to attempt to handle an unknown error.

### 6) Tools to easily access the framework through higher level languages

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
7. Minimal effort should be put in by the maintainer of these abstractions in order to shorten the distance between the framework's code and the
app developer.

### 7) Ideally use native components from IOS and Android

This is what'll make pure Zig difficult.

## Roc Lang

Roc is the high level language that I want to use for "official" support.
- It's aiming to be as fast as Go in both speed and compilation.
- It natively allows for hot reload and code push.
- It's being built for the server so you can use this for both frontend and backend.
- It's quick and easy to write.
- It's immutable by default which is a feature in pretty much every frontend statemanagement library/standard.

Since Roc is very new, this is very subject to change; but if it works, I believe it can create advantages that no other non-js framework can compete with.
