# YearOfTheRabbit-CTF
 Year Of The Rabbit Ctf Solution

# Necessary tools

* Nmap
* Hydra
* Dirsearch
* Dirbuster

## First, we check the IP address in our browser. Then we scan for open ports with nmap.
![giriştarama](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/5def245f-d5ea-418b-abcc-db6298f73530)


## As a result of the scan, ports 21, 22 and 80 are open
![nmaptarama](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/1db102af-5105-4615-8a11-1cee73aee4dc)

## We use our 'Dirsearch' tool because we can't find any information.
![dirsearch](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/6aa62278-b13a-4bd2-99ec-e3c8ff94ab40)

## A hidden page called 'assets' was found here. Now we go to the url it gave us in our browser.
![assets](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/a2e35ca8-dda5-4f4a-ae97-9c2cc03cfa24)

## When we enter the 'Style.css' file, we see a hidden '.php' file line. We also check from our browser and it redirects to You Tube channel.
## While redirecting, web pages are going through, now we click 'Inspect' to look at it and click on the 'Network' tab from there.
![networkdirectory](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/ef1ae623-65b1-4ebf-bf0c-d39b7357eb88)

### We see that it is the username 'ftpuser'. Now, to find the password, let's save the passwords in a .txt file by saying 'nano wordlist.txt'. Now, let's try to find the password by typing the command 'hydra -l ftpuser -P wordlist.txt ftp://10.10.96.186 -V' with the 'Hydra' tool.
![hydrapasw](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/10e5f10b-fcd7-4e4c-9e5f-323ac7014e34)

# Now let's try logging in via 'FTP' with username and password.
![ftpip](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/6867b667-f364-4f56-bfbc-bbfbdf049d3f)

## We log in to ftp by entering the username and password via ftp. Then let's check it by saying 'ls -la'.
![ftpls-la](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/4ee22e68-9a81-4c4d-97da-d27ce3445030)

## Let's download the file named Eli's_Creds.txt to the locale by saying 'get Eli's_Creds.txt'. Now let's look at the file contents by saying 'cat Eli's_Creds.txt'.

![catElis](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/5211ff7b-c5a8-4440-ae24-36ccbd3246e1)

## It contains Cipher text. When we searched in which language this article was written, we learned that it was Brainfuck. Let's try to translate it by saying Brainfuck decoder in our browser.
![Brainfuct](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/423a7774-c731-4957-ae39-05b2e971333a)

### As a result of the translation process we perform in our browser, Eli's Username and password are displayed. Then, by saying 'ssh eli@10.10.96.186', we enter ssh with the username and password as in the picture above.
![ssheli](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/76bbaa56-6ad4-4fb5-ba1f-d8fbc10a48ef)

## Here we see a message and the keyword is 's3cr3t'. Let's search for such a folder by saying 'locate s3cr3t'. After the folder is found, let's go to the 's3cr3t' folder.
![locates3cr3t](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/b8ed7aa2-2ddf-4f5d-8d50-58f8ee1c6942)

### When we logged in, he gave us the Gwendoline username and password. After logging in as Gwendoline, we see that there is a user.txt file under the gwendoline folder. We find our flag by saying 'cat user.txt'.
![usertxtflag](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/b3bde3c2-b71f-4794-a4ae-b24d3920e961)

## Let's run the command 'sudo –u#-1 /usr/bin/vi /home/gwendoline/user.txt'. As a result, we see that there is a folder named root, and when we log in by saying 'cd root', there is a 'root.txt' file under the folder. Here we found our wanted Flag. Now, we looked at the file contents with the 'cat root.txt' command and caught the flag. 
# CONGRATULATIONS!!!
![roottxt](https://github.com/bahtyyarabayev/YearOfTheRabbit_CTF/assets/92421009/f5c3c1da-fa26-426c-91f3-d0121e64b2fe)
