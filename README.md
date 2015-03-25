# Wifish

Wifish (from wifi.sh) is meant to be very little. Design Goals are

1. List Available Wifi APs
2. Connect to an AP

That is all.

## Requirements

1. iw and wpa\_supplicant.
2. gawk - Sorry other awks, Multidimensional arrays make this much cleaner.

## Usage

### Get it
clone this repo
```
git clone git://github.com/bougyman/wifish
```

### Configure it

*Optional* Populate /etc/wifish/interface with your interface name


### Use it

#### Make sure wpa\_supplicant is running and you have access

```
wpa_cli status
```

If this errors, FIX IT BEFORE GOING ANY FURTHER, NOTHING ELSE WILL WORK

Common fixes:

1. Start wpa\_supplicant Example: `wpa_supplicant -B -c /etc/wpa_supplicant/wpa_spplicant.conf -i wlan0`
   You may need to modify your conf file location as well as interface, and this must be done as root or with sudo
2. Make sure you have rights to the wpa\_supplicant control socket, take a look a the first few lines of wpa\_supplicant.conf
   and it should be clear what group you have to be in. Of course you can always just run wifish as root (But don't)
3. Read some docs
4. See Support, below

Now run wifish

```
cd wifish
./wifish
```

This should list all available APs. If you didn't populate /etc/wifish/interface you need to pass -d Interface where Interface is the name of your wifi interface

```
./wifish -d Wifi
```

Without arguments is the same as the `list` command.

```
./wifish -d Wifi list
```

## Commands

#### Currently implemented

* list - Lists all available APs (from iw scan)
* help - shows the usage, `wifish -h`

#### In Testing

* connect - Connects to an AP
  `wifish connect MySSID`

Currently works when connecting to WPA-PSK and WPA2-PSK with or without TKIP

## Support

file a gh issue or catch me on #voidlinux on the Freenode IRC Network

