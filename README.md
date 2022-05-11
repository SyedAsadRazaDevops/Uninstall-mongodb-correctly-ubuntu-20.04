# Uninstall-mongodb-correctly-ubuntu-20.04

Please follow the below steps, it should work.
** 1 - Uninstall current installation completely**

>Source - official instructions
```
sudo service mongod stop
```
>Remove Packages
```
sudo apt-get purge mongodb-org*
```
>Remove the folders
```
sudo rm -r /var/log/mongodb
```
```
sudo rm -r /var/lib/mongodb
```

** 2 - Another option is to run the following command** 
 >which will list all packages that contain mongo in their names or their descriptions:
```
dpkg -l | grep mongo
```
>In summary, I would do (to purge all packages that start with mongo):
```
sudo apt purge mongo*
```
and then (to make sure that no mongo packages are left):
```
dpkg -l | grep mongo
```

** 3 - First, remove MongoDB from previous if installed:**
```
sudo apt remove --autoremove mongodb-org
```
>Remove any mongodb repo list files:
```
sudo rm /etc/apt/sources.list.d/mongodb*.list
````
```
sudo apt update
```
** Sometimes this works;**
```
sudo apt-get install mongodb-org --fix-missing --fix-broken
```
```
sudo apt-get autoremove mongodb-org --fix-missing --fix-broken
```


** 4 - Run this command to reload the daemon:**
```
sudo systemctl daemon-reload
```
>After this you need to restart the mongod service:
```
sudo systemctl start mongod
```
>To verify that MongoDB has started, run:
```
sudo systemctl status mongod
```

** 5 - How to remove a apt-key which I have added?**
>When I do 
```
sudo apt-key list 
```
it prints out few things on the console. Not sure which one is related to what I did above?
>LIKE / EXAMPLE
```
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <master@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <image@ubuntu.com>
```
>Remove it by running:
```
sudo apt-key del D50582E6
```
>if you are wondering what is key, use last 8 letters together from the last two blocks out of ten blocks.
> like D38B4796 from EB4C 1BFD 4F04 2F6D DDCC  EC91 7721 F63B D38B 4796

[LINK]: https://askubuntu.com/questions/604988/how-to-remove-a-apt-key-which-i-have-added

[LINK]: https://stackoverflow.com/questions/48092353/failed-to-start-mongod-service-unit-mongod-service-not-found






