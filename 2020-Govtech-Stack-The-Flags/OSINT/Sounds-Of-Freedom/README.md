# OSINT - Sounds of freedom!

## Description
```
In a recent raid on a suspected COViD hideout, we found this video in a thumbdrive on-site. We are not sure what this video signifies but we suspect COViD's henchmen might be surveying a potential target site for a biological bomb. We believe that the attack may happen soon. We need your help to identify the water body in this video! This will be a starting point for us to do an area sweep of the vicinity!

Flag Format: govtech-csg{postal_code}
```

The zip file containing all OSINT files can be found [here](https://public-download-files-9vj6yp3nvf-cat-3.s3-ap-southeast-1.amazonaws.com/OSINT+Challenge.zip).

## Solution
This was a rather easy challenge for our team, as we had a geography expert who was on the National Geography Team. Knowing that Singapore had a very limited number of water bodies, especially one of that size as seen from the video, we only had to check a few places. 

According to our resident expert, the building from which the video was taken was likely to be constructed in the late 2000s, supported by the colour palette of building and the HDB seen in the back. Moreover, based on the bus stop seen on the roadside, it was the standard design used since the mid 2000s, suggesting that this building was in a relatively new neighbourhood, such as Punggol and Sembawang.

From there, a quick search on Google Maps brought us to [Punggol Park](https://www.google.com.sg/maps/place/Punggol+Park/@1.3768635,103.8972405,619m/data=!3m1!1e3!4m5!3m4!1s0x31da163beca5d721:0xe869e5868a79ea59!8m2!3d1.3769802!4d103.8986585). Our suspicions was confirmed by the red pavilion, seen in the video, which was present in Punggol Park. This gave us the postal code: `538768`.

![Image](https://github.com/natashatyt888/Writeups-for-CTF/blob/main/2020-Govtech-Stack-The-Flags/OSINT/Sounds-Of-Freedom/Screenshot_1.png)

### Double checking the location
In order to double check and ensure we had the correct water body, we used [Google Street View](https://www.google.com.sg/maps/@1.3758911,103.8997006,3a,60y,90t/data=!3m6!1e1!3m4!1stWlDZoranZLR3DSzkQ0EvQ!2e0!7i16384!8i8192), which showed us that the architecture of the buildings at **475 Upper Serangoon Cres** matched what was seen in the video. The bus stop seen across the road also matched what was seen in the video.

#### Building Architecture
![Image](https://github.com/natashatyt888/Writeups-for-CTF/blob/main/2020-Govtech-Stack-The-Flags/OSINT/Sounds-Of-Freedom/Screenshot_2.png)

#### Bus Stop
The red pavilion can also be seen in the background based on the Google Street View.

![Image](https://github.com/natashatyt888/Writeups-for-CTF/blob/main/2020-Govtech-Stack-The-Flags/OSINT/Sounds-Of-Freedom/Screenshot_3.png)

## Flag
`govtech-csg{538768}`
