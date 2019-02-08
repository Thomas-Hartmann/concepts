# Network
#### NFS (Network File System)
To access data stored on another machine (i.e. a server) the server would implement NFS daemon processes to make data available to clients. The server administrator determines what to make available and ensures it can recognize validated clients.
From the client's side, the machine requests access to exported data, typically by issuing a mount command. If successful, the client machine can then view and interact with the file systems within the decided parameters.
[Setup NFS](https://askubuntu.com/questions/7117/which-to-use-nfs-or-samba)
[Setup NFS ubuntu](https://help.ubuntu.com/lts/serverguide/network-file-system.html.en) AND [digital ocean guide](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-16-04)
- Install `sudo apt-get install nfs-common` on the client machine to get nfs functionality without the server overhead.
- on server `/etc/exports`: 
```
/volume1/files  10.0.0.0/20(rw,async,no_wdelay,crossmnt,insecure,no_root_squash,insecure_locks,sec=sys,anonuid=1025,anongid=100)
/volume1/music  10.0.0.0/20(rw,async,no_wdelay,crossmnt,no_root_squash,insecure_locks,sec=sys,anonuid=1025,anongid=100)
/volume1/photo  10.0.0.0/20(rw,async,no_wdelay,crossmnt,no_root_squash,insecure_locks,sec=sys,anonuid=1025,anongid=100)
/volume1/video  10.0.0.0/20(rw,async,no_wdelay,crossmnt,insecure,no_root_squash,insecure_locks,sec=sys,anonuid=1025,anongid=100)
~```