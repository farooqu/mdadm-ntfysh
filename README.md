# ntfy.sh notifications for mdadm

The `mdadm-ntfy` script is a little program that handles displaying
notifications from `mdadm --monitor` by using ntfy.sh.

It handles the following notifications (from `mdadm(8)`):

| Notification | Message priority |
|--------------|----------|
|`DeviceDisappeared`| urgent |
|`RebuildStarted`| default |
|`RebuildNN`| default |
|`RebuildFinished` | default |
|`Fail`| urgent |
|`FailSpare`| urgent |
|`SpareActive`| default |
|`NewArray`| default
|`DegradedArray` | urgent |
| `MoveSpare` | default |
| `SparesMissing` | urgent |
| `TestMessage` | low |

Message priority and behavior is defined in the [ntfy.sh documentation](https://docs.ntfy.sh/publish/#message-priority).

## Installation

* Put the script somewhere, ensure it's owned by root and executable
* Create a mdadm-ntfy.token file containing an [Access token](https://docs.ntfy.sh/config/#access-tokens) if you'd like to use one
* Override the NTFY_SERVER or TOPIC variables if you want. They default to ntfy.sh and mdadm.
* Set the `PROGRAM` option in `mdadm.conf` to point to this script
* (Re)start the mdadm or mdmonitor service

## Usage

Sit back and relax, you'll see notifications pop up like:
![notification-rebuild](screenshots/notification-rebuild.png "Rebuild notification")
