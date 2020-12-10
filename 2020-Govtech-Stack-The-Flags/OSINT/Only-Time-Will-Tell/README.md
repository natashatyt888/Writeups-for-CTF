# OSINT - Only time will tell!

## Description: 
```
This picture was taken sent to us! It seems like a bomb threat! Are you able to tell where and when this photo was taken? This will help the investigating officers to narrow down their search! All we can tell is that it's taken during the day!

If you think that it's 7.24pm in which the photo was taken. Please take the associated 2 hour block. This will be 1900-2100. If you think it is 10.11am, it will be 1000-1200.

Flag Example: govtech-csg{1.401146_103.927020_1990:12:30_2000-2200}

Flag Format: govtech-csg{lat_long_date_[two hour block format]}
Use this calculator!

Addendum:
- The amount of decimal places required is the same as shown in the example given.
- CLI tool to get something before you convert it with the calculator.
```

The zip file containing all OSINT files can be found [here](https://public-download-files-9vj6yp3nvf-cat-3.s3-ap-southeast-1.amazonaws.com/OSINT+Challenge.zip).

The link for the calculator in the description can be found [here](https://www.pgc.umn.edu/apps/convert/).


## Solution

### Image provided

The image given for this challenge features a sign that reads "Speaker's Corner", which is known to be situated in Hong Lim Park in Singapore. There's also a barcode at the bottom left, which when scanned gave the date when the photograph was taken.

![OSINT 6](https://github.com/natashatyt888/Writeups-for-CTF/blob/main/2020-Govtech-Stack-The-Flags/OSINT/Only-Time-Will-Tell/osint-challenge-6.jpg)

### Step 1 - Linux exiftool to find latitude and longitude

Using Linux to run the `exiftool osint-challenge-6.jpg` terminal command, we were able to find the Degrees Minutes Seconds (DMS) of the location of the sign.

```
GPS Latitude: 1 deg 17' 11.93" N
GPS Longitude: 103 deg 50' 48.61" E
```

![Step 1](https://github.com/natashatyt888/Writeups-for-CTF/blob/main/2020-Govtech-Stack-The-Flags/OSINT/Only-Time-Will-Tell/Step%201.png)


Next, we used the [website](https://www.pgc.umn.edu/apps/convert/) suggested to us to find the Decimal Degrees (DD), using the DMS and obtained the following results. Referring to the examples provided, we were required to leave the latitude and longitude to **6 significant figures**.

```
Latitude: 1.286647°
Longitude: 103.846836°
```

![Step 1 p2](https://github.com/natashatyt888/Writeups-for-CTF/blob/main/2020-Govtech-Stack-The-Flags/OSINT/Only-Time-Will-Tell/Step%203.png)

This gave us the first part of the flag:
`govtech-csg{1.286647_103.846836_`

### Step 2 - Scan barcode to find the date

After fining those coordinates, we had to isolate the barcode, which was done by zooming in and taking a screenshot, and obtained this rather blurry image.

![barcode](https://github.com/natashatyt888/Writeups-for-CTF/blob/main/2020-Govtech-Stack-The-Flags/OSINT/Only-Time-Will-Tell/Step%202%20p1.png)

Using an [online barcode reader](https://online-barcode-reader.inliteresearch.com/), we uploaded the image to the website and scanned it, to obtain the date "25 October 2020", giving us the second part of the flag. As we were required to order the date in the format **YYYY:MM:DD**, the flag now looks like that:
`govtech-csg{1.286647_103.846836_2020:10:25_`

### Step 3 - Finding time
Lastly, we had to find the time which the picture was taken, given in a **2-hour time frame**. As we had unlimited attempts, we decided to brute force the time, as we were certain that everything else was correct. Based on the shadows in image, it looked to be early afternoon. Thus, we started from 1200-1400, and quickly found the flag, which was `1500-1700`. With that, we had found every part of the flag, giving us the complete flag:

`govtech-csg{1.286647_103.846836_2020:10:25_1500-1700}`

## Flag
`govtech-csg{1.286647_103.846836_2020:10:25_1500-1700}`
