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

### Step 1 - Linux exiftool to find lat and long
Only time will tell: exiftool the image to find the lat & long & confirmed it by googling for the lat & long, 

### Step 2 - Scan barcode to find the date
scan barcode to get the date of 25 Oct 2020

### Step 3 - Finding time
bruteforced the time, started past 12 due to the shadows on the ground 

## Flag
`govtech-csg{1.286647_103.846836_2020:10:25_1500-1700}`
