Installed Virtualbox https://www.virtualbox.org/wiki/Downloads Windows hosts (went with Default directories and options)  
Created a 64bit Linux VM with (Screens)  
Started the virtual machine and mounted the downloaded file debian-live-11.2.0-amd64-xfce+nonfree.iso image.  
Booted to Debian GNU/Linux Live (kernel 5.10.0-10-amd64) (Screen)  
Tried out the menus and Browser. All good.  
Ran the Installer from Desktop.   
Language: American English  
Location: Helsinki  
Keyboard: Default Finnish  
Partitions  
Erase Disk: \[X\]  
Encrypt system: \[\]  
Boot loader location: Master Boot Record of VBOX HARDDISK (/dev/sda)  
  
Fill in user and computer details + password  
Log in automatically without asking for the password: \[\]  
Checked details in the Summary. All good.  
Install...  
Install...  
Install...  
Took 15 minutes but finally finished.  
Reboot and go (screen)  
Login succesful, Internet works, Apps open.  
CTRL+ALT+T to open Terminal  
Update package manager info: sudo apt-get update  
Upgrade everything: sudo apt-get -y dist-upgrade  
10 minutes later it's done. Reboot as the Linux kernel was upgraded.  
Survided the reboot and logged back in.  
Opened terminal and used Debian's built in tasksel to install Cinnamon desktop environment. Might be a bit heavier but I'm used to it.
* sudo tasksel, choose your flavor with arrow keys and Spacebar then continue with Enter

Seuraava tehtävä.  
sudo lshw -short -sanitize palautti virheen:   
sudo: lshw: command not found  
sudo apt-get install lshw  
sudo lshw -short -sanitize  
Palautuu lista työaseman laitteista.  
Ensimmäinen kolumni ilmoittaa portin johon laite on kytketty.  
Toinen kolumni ilmoittaa laitteen mount pointin Linuxin tiedostojärjestelmän sisällä.
Kolmas kolumni on laitteen tyyppi  
Neljännessä tarkemmat laitetiedot.  

Sovellusasennuksia
Taskwarrior
sudo apt-get install taskwarrior
<img src="Pictures/taskwarriorTest.png">

https://taskwarrior.org/docs/start.html
https://taskwarrior.org/docs/commands/

Vivaldi selain
Ladataan asennustiedosto (curlin -o handle määrittää, että kohde ladataan koneelle):
curl -o https://downloads.vivaldi.com/stable/vivaldi-stable_5.0.2497.48-1_amd64.deb
Asennetaan (-i = install):
sudo dpkg -i vivaldi-stable_5.0.2497.48-1_amd64.deb
Päädytään virheeseen, koska vivaldin asennus on riippuvainen wget istä.
sudo apt-get install wget
sudo dpkg -i vivaldi-stable_5.0.2497.48-1_amd64.deb
<img src="Pictures/vivaldiTest.png">

Flameshot kuvakaappaustyökalu
sudo apt install flameshot
<img src="Picture/flameshotTest.png">

Lisensseistä
Taskwarrior
The MIT License (https://www.opensource.org/licenses/mit-license.php)
https://taskwarrior.org/docs/license.html

Vivaldi
Ei ole minkään yhden Open Source lisenssin alla.
Muutokset Chromium lähdekoodiin tehty BSD lisenssin mukaisesti ja Vivaldi tarjoaa käyttöliittymänsä koodin selkomuodossa luettavaksi.

Flameshot
Pääkoodi käyttää GPLv3 (GNU General Public License v3) lisenssiä
Logo Free Art Licence v1.3
Painikkeiden ikonit Apache License 2.0
https://flameshot.org/docs/overview/overview/