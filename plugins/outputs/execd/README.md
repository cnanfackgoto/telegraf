# Execd Output Plugin

The `execd` plugin runs an external program as a daemon.

Telegraf minimum version: Telegraf 1.15.0

## Configuration

```toml @sample.conf
# Run executable as long-running output plugin
[[outputs.execd]]
  ## One program to run as daemon.
  ## NOTE: process and each argument should each be their own string
  command = ["my-telegraf-output", "--some-flag", "value"]

  ## Environment variables
  ## Array of "key=value" pairs to pass as environment variables
  ## e.g. "KEY=value", "USERNAME=John Doe",
  ## "LD_LIBRARY_PATH=/opt/custom/lib64:/usr/local/libs"
  # environment = []

  ## Delay before the process is restarted after an unexpected termination
  restart_delay = "10s"

  ## Flag to determine whether execd should throw error when part of metrics is unserializable
  ## Setting this to true will skip the unserializable metrics and process the rest of metrics
  ## Setting this to false will throw error when encountering unserializable metrics and none will be processed
  # ignore_serialization_error = false

  ## Data format to export.
  ## Each data format has its own unique set of configuration options, read
  ## more about them here:
  ## https://github.com/influxdata/telegraf/blob/master/docs/DATA_FORMATS_OUTPUT.md
  data_format = "influx"
```

## Example

see [examples][]

[examples]: examples/
