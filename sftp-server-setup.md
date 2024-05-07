# Setting Up a Local SFTP Server

This guide will walk you through the process of setting up a local SFTP (Secure File Transfer Protocol) server on your machine. Follow the steps below to get started.

## Prerequisites

Before setting up the SFTP server, ensure that you have the following prerequisites:

- [ ] Operating system: The instructions provided in this guide are applicable to Linux-based systems. Adjustments may be required for other operating systems.
- [ ] Root access or sudo privileges: You need administrative privileges to install and configure software on your machine.

## Step 1: Install OpenSSH Server

The OpenSSH server allows secure remote access and file transfers. To install it, follow these steps:

1. Open a terminal or command prompt.
2. Update the package list by running the following command:
    ```bash
    sudo apt update
    ```

3. Install the OpenSSH server package by executing the command:
    ```bash
    sudo apt install openssh-server
    ```

4. During the installation process, you may be prompted to confirm. Press `Y` or `Enter` to proceed.

## Step 2: Configure the SFTP Server

After installing the OpenSSH server, you need to configure it to enable SFTP access. Follow these steps:

1. Open the SSH server configuration file using a text editor. For example:
    ```bash
    sudo nano /etc/ssh/sshd_config
    ```

2. Locate the following line in the file:
    ```
    #Subsystem sftp /usr/lib/openssh/sftp-server
    ```

3. Uncomment the line by removing the `#` at the beginning:
    ```
    Subsystem sftp /usr/lib/openssh/sftp-server
    ```

4. Save and close the file.

## Step 3: Restart the SSH Server

To apply the changes made to the SSH server configuration, you need to restart the SSH service. Perform the following steps:

1. Restart the SSH server by running the command:
    ```bash
    sudo service ssh restart
    ```

2. If prompted, enter your password or confirm the action to restart the SSH service.

## Step 4: Create an SFTP User

To enable SFTP access, you'll need to create a separate user account for the SFTP server. Follow these steps:

1. Open a terminal or command prompt.

2. Create a new user account by executing the command:
    ```bash
    sudo adduser sftpuser
    ```

3. When prompted, enter a password for the new user and provide any additional information if required.

4. Verify the new user's access by attempting to log in to the SFTP server using the new account:
    ```bash
    sftp sftpuser@localhost
    ```

    If you can establish a connection and log in successfully, the SFTP server setup is complete.

## Step 5: SFTP Server Usage

Once the SFTP server is set up and a user is created, you can use any SFTP client to connect to your local SFTP server. Here are some common SFTP clients:

- [FileZilla](https://filezilla-project.org/)
- [WinSCP](https://winscp.net/eng/index.php)
- [Cyberduck](https://cyberduck.io/)

To connect to your SFTP server using an SFTP client, use the following details:

- Host/Server: `localhost`
- Port: `22`
- Username: The username you created in Step 4
- Password: The password you set for the user

## Conclusion

You have successfully set up a local SFTP server on your machine. This allows secure file transfers between your computer and other devices. You can now use an SFTP client to connect to your server and transfer files securely.

Note: Ensure that you take appropriate security measures, such as configuring firewall rules and applying access restrictions, to protect your SFTP server.

Ref: https://www.youtube.com/watch?v=pQtbsZHmmdo