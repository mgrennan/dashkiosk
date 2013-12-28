DashKiosk
=========

This is a simple Android application whose purpose is to display
fullscreen non-interactive dashboards on Android devices. Its main use
is to be run from an Android stick plug on some TV to display a
dashboard (hence the name).

Features
--------

 - Fullscreen webview with no possible interaction.
 - Can be setup as an home screen to be run when the device starts.
 - Prevent the device to go to sleep.
 - Configuration is load from some remote server.

Customization
-------------

Some customization needs to be done at compile time. If you want to
change the loading screen, have a look at `assets/html/loading.html`
as well as the linked files `assets/stylesheets/loading.css` and
`assets/images/loading.svg`.

You can change the URL to ping to get the list of URL to display in
`res/xml/preferences.xml`. Those preferences settings are not
available at runtime unless you trigger the activity manually. For
example, with `adb`:

    adb shell am start -n \
       com.deezer.android.dashkiosk/com.deezer.android.dashkiosk.DashboardPreferences

Ping URL
--------

The ping URL should return a list of URL in a specially crafted JSON
message. This list is an array of URL objects. An URL objects has one
mandatory field, `url` which is the URL to be loaded. The accepted
fields for an URL object are:

 - `url`: the URL to be loaded
 - `delay`: the delay in seconds this URL should be displayed, default
   to 0 which means display the URL forever.

An example of such a list is provided in `examples/dashboards.json`.