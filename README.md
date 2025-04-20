# port

Determine if a host is accessible on a given TCP port.


# To install

To install into the default `/usr/local/bin` directory:

```sh
make install
```


# Examples

Determine if the ssh port on github.com is accessible.
No output is produced.  A 0 exit code insides access.

```sh
$ /usr/local/bin/port github.com
```

Use the port command to determine of TCP port 80 for www.github.com is accessible:

```sh
$ if /usr/local/bin/port www.github.com 80; then
    echo "Yes, TCP port 80 for www.github.com is accessible."
fi
```

Determine if TCP port 443 (https) on www.google.com is accessible,
with some additional verbosity:

```sh
$ /usr/local/bin/port -v 1 www.google.com 443
```

Determine if TCP port 12345 on nowhere.example.com is accessible
with even more verbosity.  Wait up to 2.5 seconds for the host to respond:

```sh
$ /usr/local/bin/port -v 3 -t 2.5 nowhere.example.com 12345
```


# Usage

```
/usr/local/bin/port [-h] [-v level] [-V] [-t timeout] host [port_num]

	-h		print help message and exit
	-v level	set verbosity level (def level: 0)
	-V		print version string and exit

	-t timeout	seconds for probe timeout (def: 0.25)
			NOTE: timeout may be a floating point value
			NOTE: 0 ==> infinite time
			NOTE: If > 1, the nc -G TCP timeout will be extended as well

	host		hostname or IP address of server
	port_num	TCP port number to probe (def: 22)

Exit codes:
     0	    host port is accessible
     1	    host port is NOT accessible
     2	    -h and help string printed or -V and version string printed
     3	    command line error
     4	    missing critical tool
 >= 10	    internal error
```


# Reporting Security Issues

To report a security issue, please visit "[Reporting Security Issues](https://github.com/lcn2/port/security/policy)".
