# Firewalla
Options and settings regarding Firewalla box

Warning> This is maybe not the best idea to connect home automation to security equipement... 

Make the Firewalla play a sound on Sonos at a defined time thgough Cron jobs

https://help.firewalla.com/hc/en-us/community/posts/4429202903571-Using-Firewalla-to-broadcast-messages-to-Sonos-speakers



putty pi@192.168.xx.xx -pw vNbzQdCSS7 
Where you have the correct ip from Firewalla and the password generated through the Firwealla App (Settings > Advanced > Configurations > SSH Console > Tap on password)


First install and try soco :
    sudo apt-get update
    sudo apt-get install -y pip
    sudo -H pip install -U soco-cli 
    sonos-discover

Play mymusic.mp3 file on Kitchen speaker
    sonos Kitchen play_file mymusic.mp3

Due to the non permanent storage, we need a script to load Sonos Command Line at startup
mkdir /home/pi/.firewalla/config/post_main.d/
vi /home/pi/.firewalla/config/post_main.d/socosetup.sh
    sudo apt-get update
    sudo apt-get install -y pip
    sudo -H pip install -U soco-cli 

Use crontsab -e to edit cron jobs, or.. due to the non permanent storage, we need to prepare the cronjobs (will be refreshed at each reboot) and play mymusic mp3 in the kitchen every 5 minutes.. 
vi ~/.firewalla/config/user_crontab
    */5 * * * * /usr/local/bin/sonos Kitchen if_stopped play_file mymusic.mp3  &> /tmp/sonoscmd.log



