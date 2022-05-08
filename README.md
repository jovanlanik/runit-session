# runit-session
Manage services in a graphical session using runit.
# Installation
Install `./runit-session` and `./runit-session-service` somewhere in `$PATH`.
# Usage
The session is started by running `$ runit-session`.
It will find your session config `~/.config/runit-session/session` and source it.
This is where you setup the environment and start your Wayland compositor or Xorg.
If no config is found, `$ dbus-run-session sway` is ran.
From your compositor or session you should start `$ runit-session-service`.
This script makes copies of all services from `~/.config/runit-session/` and starts them.
After your session ends and all services exit, the copies are removed.
