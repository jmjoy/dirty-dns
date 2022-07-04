# ⚠️ Deprecated

Prefer to use coredns with [template plugin](https://coredns.io/plugins/template/), which supports matching domain by regex.

# dirty-dns

A simple and dirty dns server support match regex query name, get ip by execute command, etc.

Modify from [dnsguide sample4](https://github.com/EmilHernvall/dnsguide/blob/master/samples/sample4.rs).

## Usage

```
USAGE:
    dirty-dns [OPTIONS] --config-file <PATH>

FLAGS:
        --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
        --config-file <PATH>    Set config file.
    -h, --host <HOST>           Which host the service to listen.
        --num-thread <COUNT>    How many thread will spawn.
    -p, --port <PORT>           Which port the service to listen.
```

## Example Config

```toml
# Check query name is match left address or regexp.
[address]
'/w-(.*\.jmjoy\.top|.*\.jmjoy\.com)/' = "127.0.0.1"         # regexp surround with //
'/x-(.*\.jmjoy\.top|.*\.jmjoy\.com)/' = "env(RUST_TEST_IP)" # environment argument support
'/(.*\.jmjoy\.top|.*\.jmjoy\.com)/' = "`echo 127.0.0.1`"    # executeable command surround with ``
```

