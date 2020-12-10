# OSINT - Sounds of freedom!

## Description
```
In a recent raid on a suspected COViD hideout, we found this video in a thumbdrive on-site. We are not sure what this video signifies but we suspect COViD's henchmen might be surveying a potential target site for a biological bomb. We believe that the attack may happen soon. We need your help to identify the water body in this video! This will be a starting point for us to do an area sweep of the vicinity!

Flag Format: govtech-csg{postal_code}
```

The zip file containing all OSINT files can be found [here](https://public-download-files-9vj6yp3nvf-cat-3.s3-ap-southeast-1.amazonaws.com/OSINT+Challenge.zip).

## Solution

This time around, the file provided was a video, which probably would mean that the metadata would not be the key to solving this challenge. Let's watch the video to look for any clues that it may be hiding. First up, the prompt itself tells us that it will be a postcode of a water body. This signifcantly narrows down the areas we will have to check, since Singapore has relatively few water bodies.

#### First video frame
![first-frame](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Sounds-Of-Freedom/first-video-frame.png)

This first video frame has *many* clues hidden inside it, although it may not appear to do so at first glance.

Firstly, based on the design of the building, from the monochromatic colour scheme, to the architecture of the external supporting pillars, and dedicated balconies for air-conditioning condenser units, we can infer that the building is likely to be a HDB building constructed sometime after 2000, which all have similar design features. This is also supported by the design of the bus stop seen on the roadside, which is of a standardized design installed since the late 1990s in Singapore. We can also see that the bus stop most likely has a park behind it, as shown by the green space behind it, as well as the path and lampposts seen in it.

Thus, we can infer that the video has been shot in a relatively new neighbourhood built in the 1990s and onwards, giving us the candidates of Sengkang, Punggol, Canberra, and Jurong West. Looking at Google Maps, Canberra can be immediately eliminated from consideration, as it does not possess a park with a water body, of the suitable size. Jurong West can also be eliminated from consideration, as the Jurong Lake Gardens area is too old to match, and the area near Jurong Central Park does not have a bus stop with matching surroundings.

This leaves us with just Sengkang and Punggol to check, with 3 candidate parks - Sengkang Riverside Park, Punggol Waterway Park, and Punggol Park. Sengkang Riverside Park and Punggol Waterway Park can be eliminated next, as they do not have any bus stops in appropriate positions.

This thus leaves us with [Punggol Park](https://www.google.com.sg/maps/place/Punggol+Park/@1.3768635,103.8972405,619m/data=!3m1!1e3!4m5!3m4!1s0x31da163beca5d721:0xe869e5868a79ea59!8m2!3d1.3769802!4d103.8986585), located in.... Sengkang.

*Punggol* Park is located in *Sengkang*. ಠ_ಠ

A quick search of the postal code for Punggol Park gives us the code `538768`.

![Image](https://github.com/natashatyt888/Writeups-for-CTF/blob/main/2020-Govtech-Stack-The-Flags/OSINT/Sounds-Of-Freedom/Screenshot_1.png)

We should probably look at the rest of the video to be sure, however....

### Another clue

Looking through the rest of the video verifies our suspicions about Punggol Park being the right location, and one other video frame provides the rest of the clues needed to verify that this was indeed the right location.

![another video frame](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Sounds-Of-Freedom/opposite-blocks.png)

Firstly, the red pavillion shown in the left side of the frame can also be seen on the satellite view. [Pictures posted on Google Maps](https://goo.gl/maps/moLQPMTQUbvpBXN4A) verify this as well.

We can also see a block of blue-green buildings on the opposite side, of an older HDB design. Using Street View, [we can see that these buildings](Hougang Ave 8 - Google Maps) are probably the ones seen in the video, making this an even more likely match.

### Double checking the location
In order to double check and ensure we had the correct water body, we used [Google Street View](https://www.google.com.sg/maps/@1.3758911,103.8997006,3a,60y,90t/data=!3m6!1e1!3m4!1stWlDZoranZLR3DSzkQ0EvQ!2e0!7i16384!8i8192), which showed us that the architecture of the buildings at **475 Upper Serangoon Cres** matched what was seen in the video. The bus stop seen across the road also matched what was seen in the video.

#### Building Architecture
![Image](https://github.com/natashatyt888/Writeups-for-CTF/blob/main/2020-Govtech-Stack-The-Flags/OSINT/Sounds-Of-Freedom/Screenshot_2.png)

#### Bus Stop
The red pavilion can also be seen in the background based on the Google Street View.

![Image](https://github.com/natashatyt888/Writeups-for-CTF/blob/main/2020-Govtech-Stack-The-Flags/OSINT/Sounds-Of-Freedom/Screenshot_3.png)

## Flag
`govtech-csg{538768}`
