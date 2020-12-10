# Where was he kidnapped?

## Description
```
The missing engineer stores his videos from his phone in his private cloud servers. We managed to get hold of these videos and we will need your help to 
trace back the route taken he took before going missing and identify where he was potentially kidnapped!

You only have limited number of flag submissions!

Flag Format: govtech-csg{postal_code}
```

## Solution

As the documents were 3 video files, the clues must once again be within the content of the files themselves.

### First Video

![firstvideo](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Where-was-he-kidnapped/busnumber.png)

The first file reveals that the engineer got onto bus 117, headed towards Punggol Interchange, opposite what appears to be an MRT station. Looking at [Citymapper](https://citymapper.com) for the [route of bus 117](https://citymapper.com/singapore/bus/sbs-transit-117), we see that it passes opposite 4 MRT stations on its way to Punggol - Sembawang, Canberra, Yishun, and Khatib. Based upon the architecture of the station seen in the video, Canberra MRT station can be eliminated as it does not architecturally match the station seen in the video. Using [Street View](Yishun Ave 2 - Google Maps) to compare the locations reveals that the engineer got on the bus opposite Khatib MRT.

### Second Video

![secondvideo](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Where-was-he-kidnapped/yellow-pillars.png)

The text on the second video suggests that it was taken some distance away from Khatib MRT. Thus, it would be logical to check the bus stops starting from a couple stops from Khatib MRT station.

![citymapper](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Where-was-he-kidnapped/citymapper.png)

Looking at the video, we can see that there are prominent yellow pillars near the bus stop, and can also deduce from the architecture of both the pillars and the background building that we are still in the older section of Yishun/Khatib, which rules out any bus stop after Block 871, as the entire neighbourhood along Yishun Avenue 1 after that point was built relatively recently.

Thus, it would be logical to check each of the 3 remaining bus stops, starting from the furthest (Block 871). Going into [Street View](Yishun Ave 1 - Google Maps) at the bus stop shows the same yellow pillars as in the video - and which is absent from the other 2 bus stops, indicating that the engineer alighted here.

### Third Video

![thirdvideo](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Where-was-he-kidnapped/community-garden.png)

The third video, where the engineer was kidnapped (and whose postcode would be the flag), has some final clues that enable us to solve the puzzle. Firstly, we can see a relatively large, open field in the background, and a community garden, with a view from the void deck of a HDB block. As can be seen from the satellite view of the area, obtained on Google Maps, the only location that this could be is the blocks surrounding the field of blocks 870, 867, or 865.

![satellite](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Where-was-he-kidnapped/satellite.png)

Looking more closely at the satellite view, we can make out the outline of a community garden right next to block 870, which is also seen in the video itself. As we have a limited number of tries to get this flag right, it would be good to double-check our results. Luckily, there is Street View imagery looking at almost the same direction as the video!

![streetview](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Where-was-he-kidnapped/streetview.png)

In the Street View imagery, we can clearly see the same bench and community garden, confirming the location as **870 Yishun Street 81**, and a postal code of `760870`.

## Flag
`govtech-csg{760870}`
