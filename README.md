Jitsi Meet - Secure, Simple and Scalable Video Conferences
====
Jitsi Meet is an open-source (Apache) WebRTC JavaScript application that uses [Jitsi Videobridge](https://jitsi.org/videobridge) to provide high quality, scalable video conferences. You can see [Jitsi Meet in action](http://youtu.be/7vFUVClsNh0) here at the session #482 of the VoIP Users Conference.

You can also try it out yourself at https://meet.jit.si .

Jitsi Meet allows for very efficient collaboration. It allows users to stream their desktop or only some windows. It also supports shared document editing with Etherpad.

## Installation

Installing Jitsi Meet is quite a simple experience. For Debian-based systems, we recommend following the [quick-install](https://github.com/jitsi/jitsi-meet/blob/master/doc/quick-install.md) document, which uses the package system.

For other systems, or if you wish to install all components manually, see the [detailed manual installation instructions](https://github.com/jitsi/jitsi-meet/blob/master/doc/manual-install.md).

## Building the sources

Jitsi Meet uses [Browserify](http://browserify.org). If you want to make changes in the code you need to [install Browserify](http://browserify.org/#install). Browserify requires [nodejs](http://nodejs.org).

On Debian/Ubuntu systems, the required packages can be installed with:
```
sudo apt-get install npm nodejs-legacy
cd jitsi-meet
npm install
```

To build the Jitsi Meet application, just type
```
make
```

## Working with the library sources(lib-jitsi-meet).

By default the library is build from its git repository sources. The default dependency path in package.json is :
```json
"lib-jitsi-meet": "jitsi/lib-jitsi-meet",
```

To work with local copy you must change the path to:
```json
"lib-jitsi-meet": "file:///Users/name/local-lib-jitsi-meet-copy",
```

To make the project you must force it to take the sources as 'npm update' will not do it.
```
npm install lib-jitsi-meet --force && make
```

Or if you are making only changes to the library:
```
npm install lib-jitsi-meet --force && make deploy-lib-jitsi-meet
```

Alternative way is to use [npm link](https://docs.npmjs.com/cli/link).
It allows to link `lib-jitsi-meet` dependency to local source in few steps:

```bash
cd lib-jitsi-meet

# create global symlink for lib-jitsi-meet package
npm link

cd ../jitsi-meet

# create symlink from the local node_modules folder to the global lib-jitsi-meet symlink
npm link lib-jitsi-meet
```

So now after changes in local `lib-jitsi-meet` repository you can rebuild it with `npm run install` and your `jitsi-meet` repository will use that modified library.

If you do not want to use local repository anymore you should run
```bash
cd jitsi-meet
npm unlink lib-jitsi-meet
npm install
```

## Discuss
Please use the [Jitsi dev mailing list](http://lists.jitsi.org/pipermail/dev/) to discuss feature requests before opening an issue on Github.

## Acknowledgements

Jitsi Meet started out as a sample conferencing application using Jitsi Videobridge. It was originally developed by then ESTOS' developer Philipp Hancke who then contributed it to the community where development continues with joint forces!
