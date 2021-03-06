# GStreamer C++ Plugin Boilerplate

This git module contains template code for possible GStreamer plugin projects
with C++.

gst-plugin
	basic autotools layout and basic filter code for writing a
	GStreamer plug-in.

This code is provided under a MIT license [1], which basically means "do
with it as you wish, but don't blame us if it doesn't work". You can use
this code for any project as you wish, under any license as you wish. We
recommend the use of the LGPL [2] license for applications and plugins,
given the minefield of patents the multimedia is nowadays. See our website
for details [3].

Build "myfilter" like this:

    cd gst-plugin
    ./autogen.sh

Modify gst-plugin/src/Makefile.am to add or remove source files to build or
add additional dependencies or compiler flags or change the name of the
plugin file to be installed. Run ./autoregen.sh if changes don't take effect
automatically on 'make'.

Modify gst-plugin/configure.ac to check for additional library dependencies
or other features needed by your plugin. Run ./autoregen.sh if changes don't
take effect automatically on 'make'.

Once the plugin is built you can either install it with 'sudo make install'
(however, this will by default go into the /usr/local prefix where it won't
be picked up by a GStreamer installed from packages, so you would need to
set the GST_PLUGIN_PATH environment variable to include or point to
/usr/local/lib/gstreamer-1.0/ for your plugin to be found by a from-package
GStreamer). Alternatively, you will find your plugin binary in
gst-plugins/src/.libs/ as libgstplugin.so or similar (the extension may vary),
so you can also set the GST_PLUGIN_PATH environmen variable to the
gst-plugins/src/.libs/ directory (best to specify an absolute path though).
To enable plugins, add it to your bashrc or run the line below in your 
terminal:

    export GST_PLUGIN_PATH='/usr/local/lib/gstreamer-1.0'

You can also check if it has been built correctly with:

    gst-inspect-1.0 /usr/local/lib/gstreamer-1.0/libgstmyfilter.so


[1] http://www.opensource.org/licenses/mit-license.php or COPYING.MIT

[2] http://www.opensource.org/licenses/lgpl-license.php or COPYING.LIB

[3] http://gstreamer.freedesktop.org/documentation/licensing.html
