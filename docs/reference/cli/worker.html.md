<!-- GENERATED FILE — do not edit. Rebuilt by scripts/docs_site/generate_reference.py from apps/cli/python/openprogram_cli/_impl/parser.py. -->


# worker

Manage the persistent worker process (webui + channels). All TUI / Web UI front-ends connect to this single process, so multiple front-ends and external channels share state.

```text
usage: openprogram worker [-h] verb ...
```

## `worker run`

Run the worker in the foreground (blocking). Useful for debugging — Ctrl-C stops it.

## `worker start`

Spawn a detached worker in the background and return.

## `worker stop`

Stop the running worker (SIGTERM, escalates to SIGKILL).

## `worker restart`

Stop the running worker and start a fresh one.

## `worker status`

Show whether the worker is running, its PID, port, and uptime.

## `worker install`

Install as a login service (launchd on macOS, systemd --user on Linux, Task Scheduler on Windows). Auto-starts at login and restarts on crash.

## `worker uninstall`

Remove the system service.
