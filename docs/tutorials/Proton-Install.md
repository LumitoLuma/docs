# How to install my Proton builds on Linux

Proton release notes are available at [www.lumito.net/blog](https://www.lumito.net/blog/).

## Requiremets
- Latest Proton build (you can get it from [here](https://www.lumito.net/downloads/))

#### For scratch install only:
- [This](https://dl.lumito.net/public/projects/Proton/tools/proton) bash script
- Root (sudo) access
- Python 3
- At least 3.5 GB of disk space
- Basic Linux terminal knowledge (cd, ls, apt, sudo, tar, etc.)
- And a large cup of coffee (this will take some time)

## Installing from scratch
1. Get all the necessary files (Proton's .tar.xz and my proton bash script) and place them into a folder
2. Extract the Proton base files
3. Create the directory `/opt` if it doesn't exist (`sudo mkdir /opt`)
4. Move the recently extracted `Proton` folder into `/opt` (`sudo mv Proton /opt/`). Now you should have a `/opt/Proton` folder with Proton base files located there
5. Run `chmod +x proton` in the folder that contains my proton bash script to make sure it's executable
6. Move the proton bash script to `/usr/local/bin` (`sudo mv proton /usr/local/bin/`)
7. Install Wine. Go to [wiki.winehq.org/Download](https://wiki.winehq.org/Download), follow the instructions for your OS and make sure to **install the development package, not the stable or staging ones**. Proton doesn't require the wine executable, but it needs all of its dependencies to work properly. Meanwhile, drink the cup of coffee that you should have on your desk
8. Run `proton`. You should get something like this after a few seconds:
```
Traceback (most recent call last):
  File "/opt/Proton/proton", line 1264, in <module>
    g_session.init_session(sys.argv[1] != "runinprefix")
IndexError: list index out of range
```
9. If it shows that message, you're almost done. Finally, run `proton run` to prepare the main folder (default is `~/.proton`, you can change it if you like by modifying the `PROTON_OS_FOLDER` var in my script)
10. Go to `~/.proton` and check if there are files there (pfx folder, version, etc.). If they are, then you are done! Now download some games and run `proton run {EXEC_NAME}` to execute them. If they require install, they'll be installed on `~/.proton/pfx/drive_c/{INSTALL_DIR}`. You'll need to manually run the game, since the program doesn't create desktop shortcuts.

## Updating your existing build
1. Download my latest Proton build
2. Fully delete the `/opt/Proton` directory
3. Extract the new release into the `/opt` folder
4. Run `sudo apt update` and `sudo apt full-upgrade --autoremove --purge` to upgrade all the system packages to ensure compatibility
5. Execute `proton run` to update your `~/.proton` directory (if needed)
6. Done!

If you have any issues, feel free to contact me at [www.lumito.net/support](https://www.lumito.net/support/). Thanks for using my builds!
