# OSINT - Only time will tell!

## Description
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

![OSINT 6](https://github.com/natashatyt888/Writeups-for-CTF/blob/main/2020-Govtech-Stack-The-Flags/OSINT/Only-Time-Will-Tell/osint-challenge-6.jpg)

Looking at the image above, we've got several clear pieces of information - a barcode to read, a clearly visible sign (probably a landmark of some sort) and background buildings to identify. But first, let's start off with the easiest information to get: the EXIF data.

### Step 0 - Examine EXIF data

Using `exiftool` to pull all of the available EXIF data from the image, we get this:

![Step 1](https://github.com/natashatyt888/Writeups-for-CTF/blob/main/2020-Govtech-Stack-The-Flags/OSINT/Only-Time-Will-Tell/Step%201.png)

Looks like we have lots of information to work with, and we have an easily available creation date and time, and location data! That was definitely too easy, however. And, we can definitely tell that this data has been tampered with, as seen by the camera make. *Someone's been in here.* Best not to take all of the information seen here as authoritative, then.

The easiest information to verify would be the location, since we have a landmark to look for, so let's go ahead and verify that these coordinates we obtained are correct:
```
GPS Latitude: 1 deg 17' 11.93" N
GPS Longitude: 103 deg 50' 48.61" E
```

### Step 1 - Location verification with some Google-fu and maps

From the photograph, we can clearly see that this was taken at Speaker's Corner in Hong Lim Park, a prominent landmark in Singapore. Even if we didn't know this prior to this, a quick Google search for `"Speaker's Corner singapore"` would bring up [this Wikipedia article about Speaker's Corner](https://en.wikipedia.org/wiki/Speakers%27_Corner,_Singapore), and a [very similar image](https://cdn.i-scmp.com/sites/default/files/d8/images/methode/2019/07/12/a9cb401e-a3bb-11e9-9a3c-98259c87fba2_image_hires_125138.JPG) with the same buildings in the background.

Time to see if the coordinates from the EXIF data were correct. Putting those values into Google Maps/Earth reveals that yes, this is indeed the correct place.

|                  Speaker's Corner location                   |                      EXIF location data                      |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| ![Speaker's Corner location](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Only-Time-Will-Tell/maps-speakers-corner.png) | ![EXIF location data](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Only-Time-Will-Tell/coordinate-check.png) |

Now that we know the latitude and longitude are correct, we can put those into the [calculator in the challenge prompt](https://www.pgc.umn.edu/apps/convert/) to convert the coordinates to the proper format, and we get this:

```
Latitude: 1.286647°
Longitude: 103.846836°
```

Alright, we've got a third of the flag. Nice!

`govtech-csg{1.286647_103.846836_`

### Step 2 - Finding the date

The next most prominent thing in the photograph is that barcode, so let's try and read that. Cropping a copy of the image down to the barcode, we get this:

![barcode](https://github.com/natashatyt888/Writeups-for-CTF/blob/main/2020-Govtech-Stack-The-Flags/OSINT/Only-Time-Will-Tell/Step%202%20p1.png)

Feeding that image to [a barcode reader](https://online-barcode-reader.inliteresearch.com/), we find that it's a `Code128` barcode, with the text `25 October 2020`.

This, however, is incongruous with what we have from the EXIF data. However, as the EXIF creation date can be changed by copying a file to another drive, we're pretty sure this is the second part of the flag. Converting that to the required format of **YYYY:MM:DD**, we now have:
`govtech-csg{1.286647_103.846836_2020:10:25_`

### Step 3 - Finding the time

Finally, we've got to find the last portion of the flag, the time in a **2-hour time frame**. Since the dates given in the EXIF data are most likely wrong, we'll have to try and obtain the time by other means.
Based on the lighting conditions and shadow length, it's reasonable to assume that this photograph was taken some time in the late morning to early afternoon (probably from `1000h` to `1600h`. Although we have unlimited tries and we could certainly try to brute-force this, let's try to narrow down the possible range of times we'll have to check. The buildings in the background are pretty prominent, and looking up the locations on Google Earth reveal them to be the Parkroyal on Pickering hotel, Furama City Center hotel, and the Singapore State Courts Towers.

This would mean that the photograph was taken facing pretty much directly West, and the shadows pointing directly East. This narrows down our time range to be sometime in the afternoon, from `1400h` to `1600h`.

-----

#### Wait, why did you rule out noon and 1pm?

Glad you asked. Although Singapore is located in the timezone UTC+8, if you take a look at the world's timezones on a map, you will notice that Singapore should theoretically have been located in *UTC+7*, if the timezone was set based on geographical location. Check it out below:

![timezone map](https://upload.wikimedia.org/wikipedia/commons/8/88/World_Time_Zones_Map.png)

This means that *solar noon*, when the sun should theoretically appear overhead, occurs at *1300h*, and not *1200h*, where you would instead see a short, *westward-pointing* shadow. Thus, we can safely rule out noon, and based on the length of the shadow, we can also rule out 1300h as well.

-----

This gives us just 3 timeframes to try and brute-force, which is much better than 7. We quickly found the flag by doing so, and the correct timeframe turned out to be `1500-1700`. With that, we had found every part of the flag, giving us the complete flag:

`govtech-csg{1.286647_103.846836_2020:10:25_1500-1700}`

## Flag
`govtech-csg{1.286647_103.846836_2020:10:25_1500-1700}`
