# Forensics - Voices in the Head
## Description:
```
We found a voice recording in one of the forensic images but we have no clue what's the voice recording about. Are you able to help?

Hint:
Xiao wants to help. Will you let him help you?
```
## Solution
Upon downloading the audio file, we first listened to it, and then ran it through SSTV, which did not yield any results. After that, we used [Audacity](https://www.audacityteam.org/download/) to open the file as a spectrograph to obtain the following image, which revealed the alphanumeric string `aHR0cHM6Ly9wYXN0ZWJpbi5jb20vakVUajJ1VWI=`.

[image]

We instantly recognised it as base64, and ran it through an [online decoder](https://www.base64decode.org/) to obtain the pastebin link `https://pastebin.com/jETj2uUb`.

[image 2]


The link brought us to a pastebin containing brainfuck code, which we then ran through a [compiler](https://www.tutorialspoint.com/execute_brainfk_online.php), to obtain the phrase `thisisnottheflag`. This stumpted us for a while, and we eventually gave up until the organizers released the hint `Xiao wants to help. Will you let him help you?`

[image 3]

From there, a quick Google search lead us to the link for [Xiao Steganography](https://xiao-steganography.en.softonic.com/#:~:text=Xiao%20Steganography%20is%20a%20great,is%20only%20available%20in%20English.). After we uploaded the audio file, we had to enter a password to extract an encrypted zip file. With no other obvious options, we used the passcode `thisisnottheflag`, which gave us a zipfile. 


We attempted to extract the zipfile, but used the wrong password and obtained a blank word document. Unsure of what else to do, we chose to hexdump the file using [HxD](https://mh-nexus.de/en/hxd/), and found the flag `govtech-csg{Th1sisn0ty3tthefl@g}`.


Using that to unzip the zipfile finally gave us the flag along with a hint for a latter forensic challenge.


## Flag
`govtech-csg{3uph0n1ou5_@ud10_ch@ll3ng3}`
