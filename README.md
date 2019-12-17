# Event script which triggers an action if interface(s) bandwidth utilization threshold is exceeded

[Bwutil.slax](https://github.com/jumation/bwutil/blob/master/bwutil.slax) is a proof of concept event script which compares ingress and egress byte counters for each interface specified as a script argument in event policy definition with previous readings stored in a file. If calculated bandwidth utilization for a time-period is higher than the configured threshold, then a syslog message is sent.


## Installation

Change the highlighted logical interfaces in text editor to actual WAN/uplink IFLs:
![bwutil.slax conf](https://github.com/jumation/bwutil/blob/master/bwutil_conf.png)

..or add/remove WAN interfaces like this:
```
<arguments> {
    <name> "wan3";
    <value> "ge-0/0/7.15";
}
```
Finally, copy(for example, using [scp](https://en.wikipedia.org/wiki/Secure_copy)) the [bwutil.slax](https://github.com/jumation/bwutil/blob/master/bwutil.slax) to `/var/db/scripts/event/` directory and enable the script file under `[edit event-options event-script]`.


In case of two routing engines, the script needs to be copied to the `/var/db/scripts/event/` directory on both routing engines.


## License

[GNU General Public License v3.0](https://github.com/jumation/bwutil/blob/master/LICENSE)
