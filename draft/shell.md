# Shellwhat is the shell vs the terminal?

I think there is a big article in my pocket somewhere

explanation of the bash commands that are useful

grep to find some stuff

cat to view the entire file

vim is just a code editor I suppose

explanation of all of the default folders that are on a server/computer such as etc, var, bin 

The folders you are referring to are part of the Filesystem Hierarchy Standard (FHS), which is a set of conventions for organizing directory and file structure in Unix-like operating systems.

1. **/bin (Binary):**
    - Essential binary executables (commands) that are required for system booting and repair. Basic commands like ls, cp, mv, etc., are often located in this directory.
2. **/etc (Etcetera):**
    - Configuration files for the system and various applications. System-wide configuration files are typically stored here.
3. **/var (Variable):**
    - Variable files—data that is expected to change in size and content as the system runs. This includes log files, spool directories, and temporary files.
4. **/lib (Library):**
    - Shared libraries required for binaries located in /bin and /sbin. These libraries contain code that multiple programs may use, helping to reduce duplication and improve efficiency.
5. **/usr (Unix System Resources):**
    - Secondary hierarchy containing user binaries, libraries, and documentation. Often, user-related programs and data are stored here.
6. **/tmp (Temporary):**
    - A directory for temporary files. Programs can store temporary data here that doesn't need to persist between reboots.
7. **/dev (Device):**
    - Device files representing hardware devices and pseudo-devices. For example, /dev/sda might represent the first SCSI hard drive.
8. **/sbin (System Binary):**
    - System binaries that are essential for system administration but not required for normal user processes. Commands in /sbin are usually used by the system administrator for maintenance and repair.

what is a shim?

In the context of binaries and software development, a "shim" typically refers to a small piece of code or a program that serves as an interface between two different software components. Shims are often used to bridge compatibility gaps or to adapt one interface to another. They can be particularly useful when dealing with binary compatibility issues

this one is kind of at the kernel layer

so what the base64 command does is that Base64 encoding breaks binary data into 6-bit segments of 3 full bytes. this means three full bytes which is 24 bits. Then those 6 bit segments are represented as the 2^6 which is 64. So it just condenses like binary data

The 64 characters (hence the name Base64) are 10 digits, 26 lowercase characters, 26 uppercase characters as well as the Plus sign (+) and the Forward Slash (/). There is also a 65th character known as a *pad*, which is the Equal sign (=). This character is used when the last segment of binary data doesn't contain a full 6 bits.

The entire purpose of Base64 encoding, from adding padding to preserve 3-byte binary segments to converting binary to text using the Base64 table, is to preserve the integrity of the transmitted binary information.

it’s kind of like modding it as it is forcing some things that aren’t 

Every Base64 digit represents 6 bits of data.

There are 8 bits in a byte, and the closest common multiple of 8 and 6 is 24. So 24 bits, or 3 bytes, can be represented using four 6-bit Base64 digits.

**It's important to remember that we are not encrypting the text here.** Given Base64 encoded data, it's very easy to convert it back (decode) to the original text. We are only changing the representation of the data, i.e. encoding

At the end of the encoding process, there might be a problem. If the size of the original data in bytes is a multiple of three, everything works fine. If it is not, there may be empty bytes. For proper encoding, exactly 3-bytes of binary data is needed.

This can be useful when you need to dynamically generate a command to execute at runtime.

what’s the point in using eval??

pass it dynamic arguments although I don’t even get this at the moment

it’s exit status is what is read out when using eval

- so I think it won’t like print out things as they are running

look into some extra plugins for the shell such as zsh marks
