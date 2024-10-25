# oOS alpha

> Original code done by https://github.com/pac-ac

<h2>oOS alpha</h2>

oOS is a 32 bit, (optionally) multitasking, megalithic operating system.  It uses different text modes and graphical programs to edit files using the <b>FAT32</b> and create programs using the <b>MicroPython</b> scripting language.

Multitasking kernel programs, file allocation, graphical window manipulation, GUI desktop environment, and much more

![]()

<h2>How to run/compile</h2>

Included is a pre-compiled bootable iso image that you can use in any normal virtualization software.
To compile from source do 'sudo make run' and pray for the best. The binary will be built and QEMU will boot from the virtual disk.

You will probably need the following software packages: g++, binutils, libc6-dev-i386, qemu-system-x86_64 grub-legacy, grub2, xorriso.

If you plan on using other emulators then make sure it has piix4 ide support for storage, at least 8MB of memory, standard VGA emulation, and pc speaker support for basic audio. Emulation is the preferred way to run the OS as running it on real hardware requires a very old machine for the drivers to work, as well as a lack of concern for the data on the machine since the OS doesn't care to ask if you want to write over a pre-existing system partition, it will just do it. There is also a lack of error catching that can cause crashes, which would be annoying to deal with on real machines.

<h2>How to get audio using PulseAudio</h2>

If you're using a linux host and use pulseaudio like me, add this line <code>load-module module-native-protocol-unix auth-anonymous=1 socket=/tmp/pulse-socket</code>
to <code>/etc/pulse/default.pa</code>. Then restart pulseaudio and the settings in the makefile should work. <a href="https://stackoverflow.com/questions/59988019/emulator-pulseaudio-access-denied">(original post here)</a>

<h2>Extra</h2>
Current bugs may include, window input for scripts being janky, paint width being difficult, small GUI errors when drawing programs, and other stuff too long to list here. 

For the next major update I plan on further building the network stack and implement internet functionality, along with more advanced graphical applications and custom media encodings.

<h2>Important Command List</h2>

<br>GENERIC</br>  
<br>"echo (string)"   - print out whatever arguments were passed.</br> 
<br>"help"           - list common commands and keyboard shortcuts.</br>
<br>"clear"          - clear text from screen.</br>

<br>DRIVERS/SYSTEM</br>
<br>"sleep (int)"          - use the PIT timer to delay the system by (int) number of milliseconds.</br>
<br>"beep (int)"           - use the pc speaker to beep at (int) frequency.</br>
<br>"rmem (int)"           - read value from (int) memory address.</br>
<br>"wmem (int) (int)"     - write 2nd (int) value to 1st (int) memory address.</br>
<br>"rdisk (int) (int)"    - read from 1st (int) sector number for 2nd (int) number of bytes.</br>
<br>"wdisk (int) (string)" - write (string) data to (int) sector.</br>

<br>FILESYSTEM</br>
<br>"ls"         - list all known files and number of files currently allocated.</br>
<br>"tag"           - assign an organizational tag to given files.</br>
<br>"stat (file)"   - print out size of (file) in bytes.</br>
<br>"rm (file)" - deletes and removes (file) from filesystem. [partly broken]</br>

<br>MicroPython</br>
<br>Check <link> for documentation of included APIs</br>

