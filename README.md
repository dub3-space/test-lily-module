# Test-lily-module
a test lilypad module like this https://github.com/bacalhau-project/lilypad-module-cowsay/tree/main


## Install lilypad locally

```
OSARCH=$(uname -m | awk '{if ($0 ~ /arm64|aarch64/) print "arm64"; else if ($0 ~ /x86_64|amd64/) print "amd64"; else print "unsupported_arch"}') && export OSARCH;

OSNAME=$(uname -s | awk '{if ($1 == "Darwin") print "darwin"; else if ($1 == "Linux") print "linux"; else print "unsupported_os"}') && export OSNAME;

curl -sSL -o lilypad https://github.com/bacalhau-project/lilypad/releases/download/v2.0.0-701b8cb/lilypad-$OSNAME-$OSARCH

chmod +x lilypad
sudo mv lilypad /usr/local/bin/lilypad
```

## Run this app with lilypad

```
lilypad run github.com/dub3-space/test-lily-module:f60b1fa379b28d3d2702d55d5e0235837af61557 --module-repo https://github.com/dub3-space/test-lily-module --module-hash f60b1fa379b28d3d2702d55d5e0235837af61557 --module-path ./lilypad_module.json.tmpl
```
note that `f60b1fa379b28d3d2702d55d5e0235837af61557` is the sha of the commit I want to reference to lilypad. 
you need to change this with the commit you want to use

## PAY ATTENTION
The docker image need to be built with `--platform linux/amd64` tag otherwise lilypad won't like it 
