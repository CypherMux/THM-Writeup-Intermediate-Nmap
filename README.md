# THM-Writeup-Intermediate-Nmap

Hello everybody this will be a walkthrough through the room "Intermediate Nmap" by cmnatic. This is my first write up so any feedback would be amazing. Thank you :) 

Link to the room: https://tryhackme.com/room/intermediatenmap

STEP ONE
--------

Start up your lab machine using the "Start Lab Machine" button and wait for it to boot up.

Now that we have the IP of the target machine, let's put some of our Nmap skills to the test and enumerate it to see if it has any open ports we can exploit later down the line!

Let us start by inputting the following Nmap command as I do:

``` nmap MACHINE_IP ```

Replace the "MACHINE_IP" section with your own target machine IP as it states in the "IP address" section in your browser.
(it should be on the top right of your browser tab.)


Now that we have input the nmap command and let the tool run, the following output should be in your terminal:

<img width="897" height="456" alt="image" src="https://github.com/user-attachments/assets/08563db2-d9bd-432c-924a-f1c2f2ca7895" />

As we can see, there is currently 3 ports open on this machine, port 22, port 2222, and port 31337. All we will worry about for the time being is port 31337 as we will be using it for the next step.

STEP TWO
--------

For this next step we will use the port 31337 which is open to our advantage. In your browser, input the following URL:

``` http://MACHINE_IP:31337 ```

Again replace "MACHINE_IP" with your own target machine IP. Ignore the warning about entering the site and continue anyways and you should see this on your screen:


<img width="861" height="397" alt="11" src="https://github.com/user-attachments/assets/9d315d30-acfa-4d83-ad7c-365b1f4c69be" />

Due to the nature of TryHackMe's policy on write-ups I had put a black bar over the username and the password but the point still stands we found the info we need to obtain access to the SSH server we found earlier in this room!
This will be extremely important for what we will do in the final step.

STEP THREE
----------

Now let's use that username and password we discovered to obtain access to the target machine's SSH server. Type the following command in your terminal:

``` ssh USERNAME@MACHINE_IP ```

Again, replace the "MACHINE_IP" section with your target machine IP and replace the "USERNAME" section with the username we found in the last step. After you input the command type yes to continue connecting and then input the password we found as well into the password section as shown in your terminal.


<img width="865" height="172" alt="12" src="https://github.com/user-attachments/assets/b78c4b5b-b65f-4bed-b2eb-de7a35e7bdfc" />

After you input the username and password into the SSH server, you should see something like this:


<img width="896" height="393" alt="image" src="https://github.com/user-attachments/assets/8dc8c4bd-ec48-4a20-a915-03e823fc43ed" />

We've officially made it into the SSH server using our Nmap skills!!
This is the final stretch, now we just need to find the flag somewhere within this machines directory. Let's start by seeing if there is any files pertaining to the flag in the directory we are currently in, input the following command into the SSH server.

``` ls -a ```

We input the ```-a``` flag just in case the flag is a hidden file within this directory, as we can see there is no files which are of importance to us within the directory we started in.

<img width="902" height="263" alt="image" src="https://github.com/user-attachments/assets/6617b4bb-5931-4f3f-94c0-089954e3d6ab" />

Since that didn't work, let's try to go back a directory using the ```cd ..``` command. After you input the following command list the directories again using the ```ls``` command. Now the "user" directory seems very promising to our search for the flag. Let's direct ourselves into this directory using the ```cd user``` command and then list the current files in the directory using the ```ls``` command.


<img width="902" height="135" alt="image" src="https://github.com/user-attachments/assets/0dd48a6b-3f11-4205-9bea-7cc7c6dee335" />

<img width="353" height="148" alt="image" src="https://github.com/user-attachments/assets/4b37af65-2e0a-4c9a-b523-70e11fd38a03" />

Now look what we have here we found the flag.txt file! All we have to do now is read the file by using the command:

```cat flag.txt```

After you input the command as follows, the flag should be in your terminal!


<img width="521" height="115" alt="FLAGNMAP" src="https://github.com/user-attachments/assets/0fa00653-ee21-493d-ad5f-552c3d38ae17" />

Thank you for taking the time to read my write up and have a great day!! Enjoy this cute cat I found online it's your reward :)

<img width="600" height="375" alt="cutekitty" src="https://github.com/user-attachments/assets/db69eefd-aa74-4c14-ba7b-2d5a1690e85a" />







