# Command line how to
How to use the terminal.
## Content:
1. [Linux and commandline programs](###-Linux)
2. [Git](###-Git-bash) 
3. [Installation](###-Installation)  
4. [Convert](###-Convert)   
5. [PDF](###-PDF)  
6. [Node JS](###-NodeJS)
7. [Bash scripting](###-Bash)
8. [Network](###-Network)
9. [Raspberry Pi](###-Raspberry)
10. [Nginx](###-Nginx)
11. [MongoDB](###-MongoDB)
12. [MySQL](###-Mysql)
13. [Email and Calendar](###-Thunderbird)
14. [i3 view manager](###-i3)
15. [netcat nc](###-nc)
16. [cli translate](###-Translate)











### Linux
- Create alias'es in terminal: `sudo nano ~/.bashrc` e.g: `alias cdjava='cd path/to/java/projects'`
- Logout another user from the system
    - `who` will show all logged in users
    - `sudo pkill -KILL -u <username>` logs out the user by that username.
- Change permissions
    - `sudo chmod -R 755 <folder>` recursively change permision on the folder and all sub folders.
- Delete folder with content
    - `rm -rf <foldername>`
- Print folder structure to console: `tree` or `tree <path/to/folder>` installed with
- Create an alias. Open file `~/.bashrc` and find section with aliases. Write something ala: `alias pip=pip3`
- Show active processes: `htop`
  - from: `sudo apt-get install htop` now use `htop`
- Show all running processes:
  - `ps -A | less` pipe the process list through less for pagination. press `q` to exit.
  - pipe through grep: `ps -A | grep firefox`
  - find the process id: `pgrep firefox`
- Show processes on ports
  - `lsof -i:3000`
- Kill process running on port:
  - `kill $(lsof -t -i:3000)` or `kill -9 $(lsof -t -i:3000)` for hard kill (but probably not necessary)
- Turn on palm detection to [avoid accidental pointer jumps](https://stevenkohlmeyer.com/fixing-palm-detect-ubuntu-14-04/). 
  - `xinput set-prop 11 "Synaptics Palm Dimensions" 5, 5` and maybe also `xinput set-prop 11 "Synaptics Palm Detection" 1`
- Turn on/off nautilus desktop items: `gsettings set org.gnome.desktop.background show-desktop-icons <false/true>`
- Turn on/off nemo desktop items: `gsettings set org.nemo.desktop show-desktop-icons true/false`: additional info if not enough: 
- Show file preview in nemo file manager: [source](http://www.webupd8.org/2015/01/quick-file-previewer-gloobus-preview.html)
  - `sudo add-apt-repository ppa:nilarimogard/webupd8`
  - `sudo apt-get update`
  - `sudo apt-get install gloobus-preview`
  - `sudo apt-get install nemo-gloobus-sushi`
- publish markdown: `README.md` file locally with grip (was installed with `pip install grip` since pip is written in python).
  - go to the folder containing the README.md file and enter:
  - `grip`
remove colors from the terminal when listing files and direcotories:
- `unalias ls` : [See reference here](https://www.networkworld.com/article/3269587/linux/customizing-your-text-colors-on-the-linux-command-line.html)


#### Change how alt+tab works
- Open the ConpizConfig Settings Manager (launcher -> ccsm)
- Go to window management and click the Application Switcher (or static application switcher) and set the alt+tab for the next ...

#### Shortcuts
##### Files (explorer)
- show location bar: ctrl + l
- rename system folders
    - `sudo nano /home/thomas/.config/user-dirs.dirs`
    - I used this to rename the desktop folder and pictures, videos etc.


##### Download files from web
- Using curl
    - `curl http://example.com -o my.file -s`  
        - Downloads the html file into the my.file file (-o is --output and -s is --silent)
- Using wget
- Using svn (subversion)
    - From github this is the only way to download a sub directory
    - svn checkout https://github.com/datsoftlyngby/dat2sem2017Fall/trunk/evalueringer 
        - Above the github url was changed so that 'trunk' now replaces 'tree/master' then it works





### PDF
- Split a pdf file into many one page files:
    - `pdftk largepdfile.pdf burst`

### Package manager
The ubuntu package manager dpkg is derived from Debian linux
- To see if a package (pandoc in this case) is installed: `dpkg -l | grep pandoc`


### Installation
1. `sudo wget https://github.com/jgm/pandoc/releases/download/1.15.1/pandoc-1.15.1-1-amd64.deb` followed by   
2. `sudo dpkg -i pandoc-1.15.1-1-amd64.deb` vs   
3. `sudo apt-get install pandoc` vs   
4. `cabal install pandoc` vs   
5. `sudo dpkg -i pandoc-2.3-1-amd64.deb` when the deb is downloaded and terminal runs in download folder vs.  
    - Or just double click the .deb file and it will open Ubuntu software GUI where install button is an option. 
6. `tar xvzf $TGZ --strip-components 1 -C pandoc-2.3-linux.tar.gz` when the tar is downloaded and terminal runs from same folder
WHAT ARE THE PROS AND CONS?

### Convert
- `pandoc test1.md -f markdown -t html -s -o test1.html` convert test1.md from -f markdown -t to html into the file: test1.html
- `pandoc test.docx -f docx -t markdown -s -o test.md`  

### Git bash
#### change remote url
To push to a different github repo.  
`git remote set-url origin git@github.com:USERNAME/REPOSITORY.git`
To find out what is the remote:
`git remote show origin`
Set default credentials for remote to github with https:
- in home folder ~/ create file .netrc
- inside enter:
```
machine github.com
login Thomas-Hartmann
password Ho3el123
```
#### remove files from last commit
`git reset --soft HEAD~1` Now the files are staged but not commited.
`git reset HEAD -- .` removes everything in the current folder recursively from staged area.
#### pull hard to override local changes
1. first do `git fetch --all`
2. then do `git reset --hard origin/master` or whatever branch.
#### remove files after changing .gitignore
- remove from repo so they will no longer be added if they were escaped in the .gitignore file
- `git rm -r --cached **/*.jar`  

#### see what's in remote before merge
`git fetch` This will take the commits from remote and add them to git **but not to the working tree**  
`git diff master origin/master` This will compare what is in git repo for origin/master with what is in the working tree for branch: master.  

### NodeJS
- `forever start script.js` Run Express server script as a Daemon in the background 
- `forever start -l forever.log -o out.log -e err.log script.js` log the output and errors to 2 log files

### Bash
[Loop](https://stackoverflow.com/questions/965053/extract-filename-and-extension-in-bash) through all .docx files in current folder
```bash
#!/bin/bash
FILES=./*.docx
echo "start script ............."
for f in $FILES
do
  echo "Processing $f file..."
  # Use pandoc on each .docx file to change it to .md file and change filename to not include .docx 
  pandoc $f -f docx -t markdown -s -o ${f%.*}.md
done
```
### Network
- `10.0.0.4:/volume1/files /home/pi/share nfs nouser,atime,auto,rw,dev,exec,suid 0   0`
Mounting from NAS server Synology to raspberry folder: `share`. In raspberry `/etc/fstab`:
```
10.0.0.4:/volume1/files /home/pi/Share nfs nouser,atime,auto,rw,dev,exec,suid 0   0
10.0.0.4:/volume1/videos /home/pi/Videos nfs nouser,atime,auto,rw,dev,exec,suid 0   0
10.0.0.4:/volume1/music /home/pi/Music nfs nouser,atime,auto,rw,dev,exec,suid 0   0
```
Then in `sudo nano /etc/samba/smb.conf`
```
[Pi Share]
comment = Pi shared folder
path = /home/pi/Share
browseable = yes
writeable = Yes
only guest = no
create mask = 0777
directory mask = 0777
public = yes
guest ok = yes

[Pi Video]
comment = Pi shared folder
path = /home/pi/Video
browseable = yes
writeable = Yes
only guest = no
create mask = 0777
directory mask = 0777
public = yes
guest ok = yes

[Pi Music]
comment = Pi shared folder
path = /home/pi/Music
browseable = yes
writeable = Yes
only guest = no
create mask = 0777
directory mask = 0777
public = yes
guest ok = yes
```
Then `sudo /etc/init.d/samba restart`
Then in the file manager: `smb://10.0.0.3`

### Raspberry
Raspberry pi specific operations here
- Overall configuration:
  - `sudo raspi-config`
- Start node red on reboot
  - `sudo systemctl enable nodered.service`


### Nginx
- Where are the host files
    - `/etc/nginx/sites-enabled` and
    - `/etc/nginx/sites-available` For all sites both active and 'dormant'
    - create a symbolic link from sites-available to sites-enabled. This means that the symbolic link can just be removed from sites-enabled when we wish to disable the site temporarily. And to re-enable it just create a new symbolic link:
      - `sudo ln -s /etc/nginx/sites-available/example_file /etc/nginx/sites-enabled/`
- Where are the default web folder
    - `/var/www/html/`
- See what are the default server
    - `grep -R default_server /etc/nginx/sites-enabled/`
- check nginx config before restart
    - `sudo nginx -t`
- restart nginx
    - `sudo systemctl restart nginx`
- Configure nginx: /etc/nginx/sites-enabled/<filename>
```yaml
upstream tomcat {
    server 127.0.0.1:8080 fail_timeout=0;
}

server {

        root /var/www/html;

        # Add index.php to the list if you are using PHP
        index index.html index.htm index.nginx-debian.html index.jsp;

        server_name www.bugelhartmann.dk bugelhartmann.dk;

        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                # try_files $uri $uri/ =404;
                # proxy_pass http://127.0.0.1:8080;
                include proxy_params;
                proxy_pass http://tomcat/;
        }
        location /nodeapps/ {
        proxy_pass http://127.0.0.1:3000/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
```

### MongoDB
- Install: [Small tutorial](https://websiteforstudents.com/install-mongodb-on-ubuntu-16-04-lts-servers/) 
- Connect from terminal `mongo -u admin -p --authenticationDatabase admin`;
- Config `sudo nano /lib/systemd/system/mongod.service`
- restart `sudo systemctl daemon-reload` and `sudo service mongod restart`

### Mysql
- Stop mysql: `sudo service mysql stop`
- 

### Vagrant
- First I had to go to BIOS and allow virtualmachine (Just the once)
- Then I had to stop Mysql server: `sudo service mysql stop` because it was taking up the port 3306 that vagrant file was forwarding.
- Starting vagrant from folder that contains Vagrantfile: `vagrant up`
- Current vagrant repos: 
    - edudata: `~/projects/kotlinProjects/Edutor/edutor/edudata`
- Now I could run the 
Example of a vagrant file:
```
# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = false
  # connect on port 13306
  config.vm.network :forwarded_port, guest: 3306, host: 3306
  config.vm.provision :shell, :path => "install.sh"
  config.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777", "fmode=666"]
  config.vm.network "private_network", ip: "10.19.17.12"
  config.vm.hostname = "edudata"
end
```

### Thunderbird
Best solution was [calDav](http://davmail.sourceforge.net/):
1. Installed caldav from [Here](https://sourceforge.net/projects/davmail/files/latest/download) downloaded the .deb file dubbleclicked it and install.
2. Followed this [instruction](http://davmail.sourceforge.net/thunderbirdcalendarsetup.html)
3. To remove annoying icon in system tray: `alt+right click icon` moved it to different workspace.
4. Password manager to insert the password: edit -> preferences -> security -> passwords -> saved passwords.
5. Automatic update to ubuntu updated Thunerbird and then the lightning add-on no longer worked. Solution: 
- Shut down thunderbird
- `sudo apt install xul-ext-lightning`
- Start thunderbird and now the calendar is back.



### i3
- Extend screen to HDMI:
  -  xrandr --output HDMI-2 --same-as eDP-1 --auto

### netcat
[netcat article](https://www.binarytides.com/netcat-tutorial-for-beginners/)
nc command is the "Swiss-army knife for TCP/IP". A 'power version' of telnet. It can:
1. create socket servers to listen for incoming connections on ports
2. transfer files from the terminal etc
3. Use as telnet: `nc -v google.com 80` then `GET index.html HTTP/1.1` and click 'enter' TWICE!
4. As socket server: `nc -l -v 1234` netcat listen verbose on port 1234.
5. socket client (e.g. from another terminal): `telnet localhost 1234`
6. create an echo server: `nc -lp 1234` and from another node on network: `nc <node name or ip> 1234`

### Translate
[github link to program](https://github.com/soimort/translate-shell)

- Simple translate (auto detects the input language)
  - `trans <word>` autodetects the language and translates to english
  - `trans :fr <phrase>` translates to french (:da for danish, :es for spanish)
  - `trans zh: <phrase>` to tell google translate that this is chinese (zh=chinese)
  - `trans fr:da 'cést la vie come sa'` put phrase or sentence in single-quote
  - `trans -b :fr "Saluton, Mondo"` -b is for brief mode (less verbose)
  - `trans :en word` use as **dictionary** when source and target-language are the same.
  - `trans -d fr: mot` the -d flag to use dictionary mode what ever language.
  - read from input file `trans -b -i input.txt :fr` use the -i flag
  - read fro std in `echo "Saluton, Mondo" | trans -b -o output.txt :fr` it writes to an output file in this example.

