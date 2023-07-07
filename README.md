# Warning:

The following guide requires the use of `sudo` and may create permanent damage to your macOS installation. This guide provides no warranty or support. **Follow these setups at your own risk.**

---

# Pre-requsites:
1. Space on your Mac's internal drive >= storage drive of your iOS device
2. External drive attached and mounted
3. macOS 12.6 or later
4. Have `sudo` access on your account

# Steps
## Give Terminal full-disk access
### For the other commands to work, you must give terminal access to your entire drive.
#### It is recommended to take away this access after you're done.
1. Open System Preferences
2. Go to Security & Privacy
3. Go to **Full Disk Access**
4. Click the lock in the bottom-left corner to unlock the settings
5. Enable the checkmark beside **Terminal**

<img width="780" alt="image" src="https://github.com/ddshd/itunes-ios-backup-external-drive/assets/17243132/b376133f-88e0-4c35-9eac-2d4f2918bb0f">

## Create new directory on your external drive to hold your existing and new backups
1. Open your drive in Finder
2. Create a folder with the name of your choosing
3. **Remember the path to this folder** - You will need to replace *[path_to_your_drive]* in the upcoming commands with this path. If your path has spaces, enclose it within quotation marks or escape characters.

## Copy existing backups to your external drive (optional)
### You will lose your existing backups if you do not complete this step

Run the following command in terminal:

```
sudo cp -r /Users/dhrumil/Library/Application\ Support/MobileSync/Backup/ [path_to_your_drive]/
```
Do not remove the trailing slash after `[path_to_your_drive]`. Ensure there is no space between `[path_to_your_drive]` and the trailing slash.
i.e. your path should look like: `/Volumes/Drive/iOSBackups/`

## Remove the existing backups directory
### **THIS WILL REMOVE ALL EXISTING BACKUPS**

Run the following command in terminal:
```
sudo rm -r /Users/dhrumil/Library/Application\ Support/MobileSync/Backup/
```

## Create a link between the folder between your external drive and the existing backup location

Run the following command in terminal:

```
ln -s [path_to_your_drive]/ /Users/dhrumil/Library/Application\ Support/MobileSync/Backup
```
Do not remove the trailing slash after `[path_to_your_drive]`. Ensure there is no space between `[path_to_your_drive]` and the trailing slash.
i.e. your path should look like: `/Volumes/Drive/iOSBackups/`

---

Now you can run backups in Finder and they will show up on your external drive. If the path to your external changes, or you disconnect it, your backup will not work.

---





# Restore back to your original backups folder
## Use the following command to restore back to the default backups directory on your OS drive

```
sudo rm /Users/dhrumil/Library/Application\ Support/MobileSync/Backup; mkdir /Users/dhrumil/Library/Application\ Support/MobileSync/Backup/
```
