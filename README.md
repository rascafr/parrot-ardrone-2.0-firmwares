# Parrot ArDrone 2.0 Official Firmwares

Since I couldn't find them easily (neither on the Parrot support page or other repositories), here are the official Parrot firmwares for the ArDrone 2.0.

I used this tool to get those files: [ardrone-batch-firmware-downloader](https://github.com/rascafr/ardrone-batch-firmware-downloader)

## ⚖️ Mandatory legal disclamer ⚖️

```
I am not related to Parrot S.A., and this repository is not supported nor endorsed by Parrot S.A.

This repository purpose is just to help people like me willing to upgrade / downgrade their drone's firmware since the Parrot support page and the download url are both nonexistent now.

Please be aware taht this may void your warranty (...but who cares if your drone has been bought in 2012). 

Use it at your own risks.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```

## Usage

- Connect the battery
- Connect to your drone's WiFi with your laptop
- Open a telnet session

```bash
telnet 192.168.1.1

#Trying 192.168.1.1...
#Connected to 192.168.1.1.
#Escape character is '^]'.
#BusyBox v1.14.0 () built-in shell (ash)
#Enter 'help' for a list of built-in commands.
```

- Write the version you target (the one you want to downgrade to)

```bash
echo "2.1.16" > /update/version.txt
```

- Write a version lower than the one you target (as if it was the drone's version so it will force the update)

```bash
echo "2.1.10" > /firmware/version.txt
```

- Exit the telnet session

```bash
exit
```

- Rename / copy the version file you want to upload (e.g. `2.1.16`)

```bash
cp FW_FILES/2.1.16-ardrone2_update.plf ardrone2_update.plf
```

- FTP upload it to the drone

```bash
ftp 192.168.1.1 5551

#Connected to 192.168.1.1.
#220 Operation successful
#Name (192.168.1.1:user):
#230 Operation successful

put ardrone2_update.plf

#200 Operation successful
#150 Ok to send data
#226 Operation successful
#10616484 bytes sent in 20.6 seconds (504 kbytes/s)

bye
```

- Disconnect the drone's battery, reconnect it, and wait for the LEDs to become red to green (might take 2 minutes)

Done!

## Credentials / Source links

https://www.drone-forum.com/forum/viewtopic.php?f=89&t=3357&sid=3f2ba4a1e013f675cf2589eead595e16#p25559

https://www.youtube.com/watch?v=2KwzoBF1YRs