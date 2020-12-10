# Hunt him down!

## Description
```
After solving the past two incidents, COViD sent a death threat via email today. Can you help us investigate the origins of the email and identify the suspect that is working for COViD? We will need as much information as possible so that we can perform our arrest!

Example Flag: govtech-csg{JohnLeeHaoHao-123456789-888888}

Flag Format: govtech-csg{fullname-phone number[9digits]-residential postal code[6digits]}
```

### Solution

Opening up the email in Visual Studio Code to look at the full contents of the message gave us this:

![email contents](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Hunt-him-down/email-content.png)

From there, the only really relevant information to getting the information we'd need for the flag would be from the sender, so let's check the DNS records for the custom domain the email was sent from, using [DNSDumpster](https://dnsdumpster.com). Doing so reveals several records, of which the TXT record is most interesting:

![dnsdumpster](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Hunt-him-down/dnsdumpster.png)

We have a username `lionelcxy`, as well as an email address `lionelcxy@protonmail.com`. This definitely looks like it could be something. Using the [Sherlock](https://github.com/sherlock-project/sherlock) tool to find social media accounts with the username `lionelcxy` yielded these sites:

![sherlock](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Hunt-him-down/sherlock.png)

Let's check the most commmon social media sites first - Twitter and Instagram.

#### Twitter

Going to @lionelcxy on Twitter yielded a profile with a default profile picture and a single tweet, making this most likely to be what we're looking for:

![tweet](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Hunt-him-down/twitter-carousell.png)

From this, we now know our target's name, or at least part of it: `Lionel Cheng`, giving us part of the flag. We can also see that the Carousell link displays a phone number of *9* digits, which is 1 more than a standard Singaporean phone number, but matches the description of the flag correctly, making this another piece of the flag that we have. So far, we have this:

`govtech-csg{LionelCheng(x?)(y?)-963672918-????????}`

#### Carousell

![carousell](https://www.carousell.sg/p/playstation-1-1045623891/)

Looking further into the Carousell listing, the only other useful piece of information that we can obtain is the target's possible rough location - somewhere near City Hall MRT station. This isn't a guarantee that his residential address will be nearby, however, as the area around City Hall MRT station is primarily commercial. It is still something to keep in mind, however.

#### Instagram

Looking at the Instagram page yielded two posts, all posted on the same day as the Tweet. This is most likely the account we're looking for.

![firstpost](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Hunt-him-down/instagram-1.JPG)

The first post shows a food cart, tagged with the location Lau Pa Sat. Consulting Google Maps reveals that this location is located not too far from Raffles Place MRT, one stop away from City Hall MRT, and comparing the architecture around Lau Pa Sat confirms that the location that the photo was taken was at the junction of Boon Tat Street/Commerce Street and Shenton Way. The caption "just minutes away" further suggests that the location we are looking for is within 10 minutes' walking distance of the target postcode.

![secondpost](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Hunt-him-down/instagram-2.JPG)

The second post yields a post with a Strava route, and a link to a Strava profile. Although the start and endpoints are not located in residential areas, this passes by Lau Pa Sat, and passes next to three residential buildings - Marina One, Marina Bay Suites, and The Sail at Marina Bay. These three buildings also happen to be within a 10 minute walk from the junction mentioned earlier. Time to shortlist these three buildings for consideration, and to take a look at the Strava profile.

#### Strava

![strava](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Hunt-him-down/strava.png)

Looking at the Strava profile gave us two different rides - one mentioned earlier in the Instagram post, and another unmentioned one. Both routes appear to pass through Marina One, and also pass by Marina Bay Suites, shaving the shortlist down to two possible buildings. Looking further into detail in the non-mentioned ride reveals a description of "Social Space closes so early. It was just at my block...". Doing a local area search on Google Maps for "Social Space" reveals that there is a cafe called "The Social Space" at Marina One, with a postcode of `018935`, thus giving us another portion of the flag, and bringing our flag up to this:

`govtech-csg{LionelCheng(x?)(y?)-96362918-018935}`

#### Finding the full name

We almost have the full flag, but we don't yet know what the `x` and `y` in `lionelcxy` stand for. None of the other profiles found in the Sherlock query returned any name other than "Lionel Cheng", this resulting in a Google search for `lionelcxy`. Other than bringing up the previously-found pages and posts, a LinkedIn profile was also found, which upon further inspection contained the same email address as the target, and had the name of "Cheng Xiang Yi", a "Freelance software engineer", with the same profile picture as the Carousell and Strava listings.

![linkedin](https://raw.githubusercontent.com/natashatyt888/Writeups-for-CTF/main/2020-Govtech-Stack-The-Flags/OSINT/Hunt-him-down/linkedin.png)

It appears that we have the full flag, which turned out to be correct!

### Flag

`govtech-csg{LionelCheng(x?)(y?)-96362918-018935}`
