# runit-session
Manage services in a graphical session using runit.
# Installation
Install `./runit-session` and `./runit-session-service` somewhere in `$PATH`.
# Usage
The session is started by running `$ runit-session`. It will find your session
config `~/.config/runit-session/session` and source it. This is where you
setup the environment and start your Wayland compositor or Xorg. If no config
is found, `$ dbus-run-session sway` is ran. From your compositor of session you
should start `$ runit-session-service`. This script copies all services in
`~/.config/runit-session/` and starts them. It's your responsibility to kill
the process (but sway does this if you just use `exec` in your config), send a
`SIGHUP`, `INT` or `TERM` to end services and cleanup. You can kill either
`runit-session-service` or the `runsvdir` child process (you'll find pid in
`$RUNIT_SESSION/pid`).
