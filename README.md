# lookie
`lookie` is the tool to help you monitor different kind of resources.

## Install

```bash
$ pip3 install --upgrade lookie
```

## Configuration

For now, configuration file should be in the place where `lookie` will execute.

The file: **lookie.config.json**

For now, only slack is supported.

```json
{
  "slack": {
    "hook": "<HOOK_URL>",
    "channel": "<SLACK_CHANNEL>"
  }
}
```

## Usage

```bash
% lookie --help
usage: lookie [-h] [--version] {ping,string,port} ...

`lookie` is the tool to help you monitor different kind of resources.

positional arguments:
  {ping,string,port}  sub-command help
    ping              ping check to host.
    string            Check string exists when accessing the endpoint.
    port              Check if port is accessible of a certain hostname.

optional arguments:
  -h, --help          show this help message and exit
  --version           Print the version of the tool.

Example: lookie --help
```

### Example

```bash
$ lookie string --url https://google.com --surname "GOOGLE" --string 'google'
String - google found in https://google.com -- GOOGLE: Yes
```

```bash
$ lookie ping --hostname 1.1.1.1 --surname Cloudflare
Ping check to 1.1.1.1/Cloudflare is ok: Yes
```

```bash
% lookie port --hostname 1.1.1.1 --surname Cloudflare --port 25
Port 25 of 1.1.1.1/Cloudflare is accessible: No
% lookie port --hostname 1.1.1.1 --surname Cloudflare --port 53
Port 53 of 1.1.1.1/Cloudflare is accessible: Yes
```
