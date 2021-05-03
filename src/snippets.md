---
layout: page
title: Code Snippets I copy and paste often
---

### Get Your Public IP

    curl -s canihazip.com


### Let Everyone Execute a Script

    chmod +x script.sh 

### View Permissions on a Script

    ls -l script.sh

### Edit Cron

    crontab -e

    and use [Crontab Guru](https://crontab.guru/every-week) to figure out details aroudn scheduling

### Run Code in BASH

    # Run Code
    # If we're on the PiTFT screen (ssh is xterm)
    if [ "$TERM" == "linux" ] ; then
      while :
        do
          sleep 10 # Let everything settle
          ./padd.sh
          sleep 1
      done
    fi

### Setup Wifi

    wpa_supplicant.conf  

    country=us
    update_config=1
    ctrl_interface=/var/run/wpa_supplicant

    network={
      scan_ssid=1
      ssid="MyNetworkSSID"
      psk="Pa55w0rd1234"
    }


### Find a File

    find / -iname "filename"

### Copy a Remote File to a Local System using the scp Command

    scp remote_username@10.10.0.2:/remote/file.txt /local/directory

Add `-r` to make it recursive to the folder.

### All the Various Date Formats in Python 


    %a	Locale’s abbreviated weekday name.
    %A	Locale’s full weekday name.
    %b	Locale’s abbreviated month name.
    %B	Locale’s full month name.
    %c	Locale’s appropriate date and time representation.
    %d	Day of the month as a decimal number [01,31].
    %H	Hour (24-hour clock) as a decimal number [00,23].
    %I	Hour (12-hour clock) as a decimal number [01,12].
    %j	Day of the year as a decimal number [001,366].
    %m	Month as a decimal number [01,12].
    %M	Minute as a decimal number [00,59].
    %p	Locale’s equivalent of either AM or PM.
    %S	Second as a decimal number [00,61].
    %U	Week number of the year (Sunday as the first day of the week) as a decimal number [00,53]. All days in a new year preceding the first Sunday are considered to be in week 0.
    %w	Weekday as a decimal number [0(Sunday),6].
    %W	Week number of the year (Monday as the first day of the week) as a decimal number [00,53]. All days in a new year preceding the first Monday are considered to be in week 0.
    %x	Locale’s appropriate date representation.
    %X	Locale’s appropriate time representation.
    %y	Year without century as a decimal number [00,99].
    %Y	Year with century as a decimal number.
    %z	Time zone offset indicating a positive or negative time difference from UTC/GMT of the form +HHMM or -HHMM, where H represents decimal hour digits and M represents decimal minute digits [-23:59, +23:59].
    %Z	Time zone name (no characters if no time zone exists).
    %%	A literal '%' character.

[Source](https://tecadmin.net/get-current-date-time-python/)

### Passwordless SSH


It is possible to configure your Raspberry Pi to allow access from another computer without needing to provide a password each time you connect. To do this, you need to use an SSH key instead of a password. To generate an SSH key:
Check for existing SSH keys

First, check whether there are already keys on the computer you are using to connect to the Raspberry Pi:

    ls ~/.ssh

If you see files named id_rsa.pub or id_dsa.pub then you have keys set up already, so you can skip the 'Generate new SSH keys' step below.
Generate new SSH keys

To generate new SSH keys enter the following command:

    ssh-keygen

Upon entering this command, you will be asked where to save the key. We suggest saving it in the default location (~/.ssh/id_rsa) by pressing Enter.

You will also be asked to enter a passphrase, which is optional. The passphrase is used to encrypt the private SSH key, so that if someone else copied the key, they could not impersonate you to gain access. If you choose to use a passphrase, type it here and press Enter, then type it again when prompted. Leave the field empty for no passphrase.

Now look inside your .ssh directory:

    ls ~/.ssh

and you should see the files id_rsa and id_rsa.pub:

authorized_keys  id_rsa  id_rsa.pub  known_hosts

The id_rsa file is your private key. Keep this on your computer.

The id_rsa.pub file is your public key. This is what you share with machines that you connect to: in this case your Raspberry Pi. When the machine you try to connect to matches up your public and private key, it will allow you to connect.

Take a look at your public key to see what it looks like:

    cat ~/.ssh/id_rsa.pub

It should be in the form:

    ssh-rsa <REALLY LONG STRING OF RANDOM CHARACTERS> user@host

Copy your public key to your Raspberry Pi

Using the computer which you will be connecting from, append the public key to your authorized_keys file on the Raspberry Pi by sending it over SSH:

    ssh-copy-id <USERNAME>@<IP-ADDRESS>

Note that for this step you will need to authenticate with your password.

Alternatively, if ssh-copy-id is not available on your system, you can copy the file manually over SSH:

    cat ~/.ssh/id_rsa.pub | ssh <USERNAME>@<IP-ADDRESS> 'mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys'

If you see the message `ssh: connect to host <IP-ADDRESS> port 22: Connection refused` and you know the IP-ADDRESS is correct, then you may not have enabled SSH on your Raspberry Pi. Run sudo raspi-config in the Pi's terminal window, enable SSH, then try to copy the files again.

Now try `ssh <USER>@<IP-ADDRESS>` and you should connect without a password prompt.

If you see a message "Agent admitted failure to sign using the key" then add your RSA or DSA identities to the authentication agent ssh-agent then execute the following command:

    ssh-add

If this does not work, you can get assistance on the Raspberry Pi forums.

Note: you can also send files over SSH using the scp command (secure copy). See the SCP guide for more information.
Adjust permissions for your home and .ssh directories

If you can't establish a connection after following the steps above there might be a problem with your directory permissions. First, you want to check the logs for any errors:

    tail -f /var/log/secure
    # might return:
    Nov 23 12:31:26 raspberrypi sshd[9146]: Authentication refused: bad ownership or modes for directory /home/pi

If the log says Authentication refused: bad ownership or modes for directory /home/pi there is a permission problem regarding your home directory. SSH needs your home and ~/.ssh directory to not have group write access. You can adjust the permissions using chmod:

    chmod g-w $HOME
    chmod 700 $HOME/.ssh
    chmod 600 $HOME/.ssh/authorized_keys

Now only the user itself has access to .ssh and .ssh/authorized_keys in which the public keys of your remote machines are stored.
Store the passphrase in the macOS keychain

If you are using macOS, and after verifying that your new key allows you to connect, you have the option of storing the passphrase for your key in the macOS keychain. This allows you to connect to your Raspberry Pi without entering the passphrase.

Run the following command to store it in your keychain:

    ssh-add -K ~/.ssh/id_rsa

[Source](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md)

### Rmate to edit Raspberry Pi
[How To](https://rohn.io/visual-studio-code-remote-file-editing-on-raspberry-pi)



### How to test the write speed of SD cards

    sudo ./sd_card_speed_test.sh /Volumes/Untitled

    [Download Script](https://github.com/biodranik/sd-card-speed-test)


### How to crash a site

Use the followingt script to sent a request for a bunch of error pages to see if the CPU can handle it.

    curl https://www.somesite.com/[3500-4201] -w "%{time_connect} | %{time_total} | %{speed_download} | %{http_code} | %{size_download} | %{url_effective}\n" -o file.txt -s
