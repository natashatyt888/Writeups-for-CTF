# Forensics - Voices in the Head
## Description:
```
We found a voice recording in one of the forensic images but we have no clue what's the voice recording about. Are you able to help?

Hint:
Xiao wants to help. Will you let him help you?
```
## Solution
Opened file in audacity as a spectrograph
Revealed an alphanumeric string 

Encoded in base64, led to a pastebin link pastebin.com/jETj2uUb
Pastebin contained brainfork code that printed "thisisnottheflag"

Use Xiao Steganography to extract an encrypted zip file with the passcode "thisisnottheflag"

Extracted with the wrong password and got a zip file
Hexdumped the zip file and found the flag govtech-csg{Th1sisn0ty3tthefl@g}
Used that string as the passcode to open the zip file to reveal a docx file with the flag


## Flag
`govtech-csg{3uph0n1ou5_@ud10_ch@ll3ng3}`
