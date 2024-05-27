
## NOT MUCH USED
`image` (string)
Docker image used for this device.

`mem` (string)

Set the amount of available RAM inside the device. If you set this option, the minimum allowed value is 4m (4 megabyte).

This option takes a positive integer, followed by a suffix of "b", "k", "m", "g", to indicate bytes, kilobytes, megabytes, or gigabytes.

`cpus` (float)

Limit the amount of CPU available for this device.

This option takes a positive float, ranging from 0 to max number of host logical CPUs. For instance, if the host device has two CPUs and you set `device[cpus]=1.5`, the device is guaranteed at most one and a half of the CPUs.

`port` (string)

Map localhost port HOST to the internal port GUEST of the device for the specified PROTOCOL. The syntax is [HOST:]GUEST[/PROTOCOL].

If HOST port is not specified, default is 3000. If PROTOCOL is not specified, default is `tcp`. Supported PROTOCOL values are: tcp, udp, or sctp. For instance, with this command you can map host's port 8080 to device's port 80 with TCP protocol: `device[port]="8080:80/tcp"`.

`bridged` (boolean)

Connect the device to the host network by adding an additional network interface. This interface will be connected to the host network through a NAT connection.

`ipv6` (boolean)

Enable or disable IPv6 on this device.

`exec` (string)

Run a specific shell command inside the device during the startup phase.

`sysctl` (string)

Set a sysctl option for this device. Only the `net.` namespace is allowed to be set. Can be set multiple times per device, each will add a new entry (unless the same config item is used again).

`env` (string)

Set an environment variable for the device. Can be set multiple times per device, each will add a new entry (unless the same variable is used again). The format is: ENV_NAME=ENV_VALUE.

`shell` (string)

Use the specified shell to connect to the device, e.g., when `kathara connect` is called.

`num_terms` (integer)

Choose the number of terminals to open for this device.