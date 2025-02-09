# PLD BYPASS/MOE DMA Bypass
TLDR: Steps to bypass MOE Device Management on Personal Learning Devices (PLDs) through reinstalling windows with local account before connecting to school account **[Updated 28 Jan. 2025]**

## Prerequisites
1) Kind of tech-savvy **(IMPORTANT!!)**
2) A USB drive
3) A PLD
4) Another computer
5) Extreme hatred for MOE DMA

## Format USB (on your other computer)
1) Download and run windows media creation tool (https://www.microsoft.com/en-us/software-download/windows10 or https://www.microsoft.com/en-us/software-download/windows11)
2) Choose "Create installation media"
3) Verify the specifications
4) Click "ISO File"
5) Set the location to save ISO file and wait for it to be created and click next
6) After completing creation, click "finish"
7) Insert USB into computer
8) Download and run Rufus (https://github.com/pbatard/rufus/releases/download/v4.6/rufus-4.6.exe)
9) Enable "list USB hard drives"
10) Beside boot selection (make sure it's "disk/iso"), click select and select the iso image
11) Wait for image scan to complete
12) Make sure the partition scheme is GPT
13) Set the file system to NTFS
14) Click "START"
15) On the popup window, click "disable bitlocker" and also make sure to create a local account named anything you want
16) Click ok
17) Click ok for all the warnings (if there are any)
18) Wait for it to burn finish
19) Eject the USB

## Boot USB
1) Boot to UEFI/BIOS on your PLD
2) Disable secure boot and change booot sequence to USB first
3) Boot from USB
4) Proceed with basic installation (keyboard (eg US-international) etc )
5) Delete all partitions starting with "drive 0" and click next
6) Wait for windows to install
7) Connect to the internet and click next

## Complete setup
1) Elevate your local account to administrator through an elevated cmd (in case you want to connect back to DMA): `net user /add [username] [password]` and then `net localgroup administrators [username] /add`
2) (OPTIONAL) If you want to connect back to DMA, you have to first enable bitlocker and then disable it before adding school account
3) Do whatever you want

## School internet password
You can find the passwords yourself through `netsh wlan show profile [SSID] key=clear` if your pld has connected to the internet before

## How to reconnect to school DMA?
1) Go settings -> accounts -> access work or school
2) Click connect
3) Click "connect to microsoft Entra" below
4) Sign in
5) DMA will slowly be enrolled
6) Reboot your PLD

## Notice
* You can disable ditblocker even after you have connected to DMA by signing in to your local account and disabling bitlocker/diable task schd/group policy/make an admin account etc

## DISCLAIMER
WE ARE AN INDEPENDENT ORGANISATION AND ARE NOT AFFILIATED WITH THE MINISTRY OF EDUCATION (MOE) OR ANY OTHER GOVERNMENTAL OR EDUCATIONAL INSTITUTIONS. PLEASE NOTE THAT WE ARE NOT LIABLE FOR ANY CONSEQUENCES RESULTING FROM THE MISUSE OF YOUR PERSONAL LEARNING DEVICES (PLDS). IT IS YOUR RESPONSIBILITY TO ADHERE TO YOUR SCHOOL’S GUIDELINES AND REGULATIONS REGARDING THE USE OF THESE DEVICES. ANY INAPPROPRIATE OR UNAUTHORIZED USE THAT LEADS TO DISCIPLINARY ACTIONS OR OTHER CONSEQUENCES IS SOLELY YOUR RESPONSIBILITY. WE STRONGLY ENCOURAGE USERS TO COMPLY WITH THEIR INSTITUTION’S POLICIES TO AVOID SUCH ISSUES. THIS IS PURELY MEANT FOR *EDUCATIONAL PURPOSES ONLY*.
