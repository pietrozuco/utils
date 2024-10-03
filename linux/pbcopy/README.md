# rpbcopy

## About

`pbcopy` is a well-known macOS utility that allows you to copy content to the clipboard from the command line. For example, running a command like `cat file | pbcopy` copies the contents of `file` to the clipboard.

If you're using a Mac and logging into a Linux machine, and you'd like to use the same clipboard functionality as macOS's pbcopy, this script allows you to pass `stdin` from the Linux machine directly to your Mac's clipboard.

This script is meant to be run **on the Linux machine** where you're working, and it sends the content back to the clipboard on your macOS machine over SSH.

## Installation

1. Copy the script to a directory in your `PATH` on the Linux machine.

2. Ensure the script is executable:

   ```bash
   chmod +x /path/to/script
   ```

3. To avoid having to enter your SSH password every time, set up SSH key-based authentication between your Linux machine and your Mac:

   ```bash
   ssh-keygen -t rsa
   ssh-copy-id your_mac_username@your_mac_ip_address
   ```

4. If your macOS username differs from your Linux username, you can set the `MACOS_USER` environment variable:

   ```bash
   export MACOS_USER=your_mac_username
   ```

## Usage

Once installed, the script can be used to copy content to your Mac's clipboard from the Linux machine:

```bash
echo "Hello from Linux" | rpbcopy
```

This will copy the string "Hello from Linux" to the clipboard on your Mac. You can also copy file content:

```bash
cat file.txt | rpbcopy
```

## Use Case

This script is particularly useful for users who frequently SSH into a Linux machine from their Mac and want to quickly copy content to their Mac's clipboard.

## Troubleshooting

If the script doesn't work as expected:

1. Ensure that SSH key-based authentication is set up and working properly.
2. Ensure that `pbcopy` is installed and accessible on your Mac.
3. Check that the correct IP address is being used (based on the SSH connection).
