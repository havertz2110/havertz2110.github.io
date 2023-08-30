---
title: "UIU CTF 2023"
description: "Writeup for UIU CTF 2023"
summary: "Writeup for UIU CTF 2023"
categories: ["Writeup"]
tags: ["Reverse","DFIR","Honors","Top tier","CTF"]
#externalUrl: ""
date: 2023-08-14
draft: false
authors:
  - 4nh
---

Hello, this is some lines for this UIUCTF 2023 contest. First, Im very happy because this is the first time I stepped into top 50 of an international contest with my team `phis1Ng__`, therefore, I think I need to write something in order to keep as a memory and to save some new ideas and techniques using this time.

Im responsible for 2 areas in my team: Misc and Osint(Rev is done after the contest), and that's all, here we go :D


# MISC
## 1. vimjail1

<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            Connect with `socat file:$(tty),raw,echo=0 tcp:vimjail1.chal.uiuc.tf:1337`. You may need to install socat.
        </p>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia; color:#FFFFFF;">
        </p>
    </span>
</div>

**Provided files: [entry.sh](https://2023.uiuc.tf/files/9ab066e6d8dc34b582242cd0ee5b54b8/entry.sh) -- [nsjail.cgf](https://2023.uiuc.tf/files/55e629783aaddfeb0725477795ac4156/nsjail.cfg)-- [vimrc](https://2023.uiuc.tf/files/73a3a3658313279c33f2fc69b50c45cf/vimrc)**


At my first try, I saw 1 thing that if I connected to the server, I would be stuck at vim environment, therefore, I couldn't type anything I couldn't get out of this as a result. So, I think we have to find something in order to get out of this ( it would pop up a flag in the end, i guess?? :D )

Because of that, I looked up at the provided files, I checked at 'nsjail.cfg' but nothing looked sus in there, so I checked the rest ones. I soonly noticed in 'vim.rc'that are very cool :dagger_knife: :
```bash
set nocompatible
set insertmode

inoremap <c-o> nope
inoremap <c-l> nope
inoremap <c-z> nope
inoremap <c-\><c-n> nope
```
We can see that vim is in `insertmode` so we have to do sth to escape it. And those 'inoremap' give me an idea of combining keywords together so that we can escape :D.

After trying for a little bit with many different combinations, finally I figured out that the combination: `<c-\><c-o>` worked :D

![](https://hackmd.io/_uploads/HkABiKRn2.png)


flag: uiuctf{n0_3sc4p3_f0r_y0u_8613a322d0eb0628}
## 2. vimjail1.5

<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            Fixed unintended solve in vimjail1
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            Connect with socat file:$(tty),raw,echo=0 tcp:vimjail1-5.chal.uiuc.tf:1337. You may need to install socat.
        </p>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia; color:#FFFFFF;">
        </p>
    </span>
</div>

**Provided files: [entry.sh](https://2023.uiuc.tf/files/55063dc423a8373f8cbc60d8aabd4ba6/entry.sh) -- [nsjail.cfg](https://2023.uiuc.tf/files/77ce241f2ff30c19cee849f65f2cf0dd/nsjail.cfg)-- [vimrc](https://2023.uiuc.tf/files/a5c49e80eb02414585d49a4815d2f004/vimrc)**



## 3. vimjail2

<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            Fixed unintended solve in vimjail1
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            Connect with socat file:$(tty),raw,echo=0 tcp:vimjail2.chal.uiuc.tf:1337. You may need to install socat.
        </p>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia; color:#FFFFFF;">
        </p>
    </span>
</div>


**Provided files: [entry.sh](https://2023.uiuc.tf/files/62b21acdeb6002bd9031cb569c43c8d4/entry.sh) -- [nsjail.cfg](https://2023.uiuc.tf/files/7787cd00e0f101d9680a52caee6b142a/nsjail.cfg)-- [vimrc](https://2023.uiuc.tf/files/35c5ace464a7bfa666295c14a2f8a9ed/vimrc) -- [viminfo](https://2023.uiuc.tf/files/bf3c336737319e16887d1b411234ae2f/viminfo)**

So this time, 

## 4. vimjail2.5
<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            Fixed unintended solve in vimjail1
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            Connect with socat file:$(tty),raw,echo=0 tcp:vimjail2.chal.uiuc.tf:1337. You may need to install socat.
        </p>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia; color:#FFFFFF;">
        </p>
    </span>
</div>

**Provided files: [entry.sh](https://2023.uiuc.tf/files/68058c49bdcc76666df0355f04887fbf/entry.sh) -- [nsjail.cfg](https://2023.uiuc.tf/files/c874fca1cbeec692a1f38e5b7cf39bd2/nsjail.cfg)-- [vimrc](https://2023.uiuc.tf/files/f0067b22797e23def853f13923eb6568/vimrc) -- [viminfo](https://2023.uiuc.tf/files/b10cd1e18dcb2013f0ab008cfebf4f8b/viminfo)**

## 6. Tornado Warning
<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
         <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        <p style="margin-left:1em; color:#FFFFFF;">
            "Check out this alert that I received on a weather radio. Somebody transmitted a secret message via errors in the header! Fortunately, my radio corrected the errors and recovered the original data. But can you find out what the secret message says?  
            Note: flag is not case sensitive."
        </p>
        <details>
            <summary style="color:#FFFFFF;">Hint 1</summary>
            <p style="margin-left:1em; color:#FFFFFF;">The header is encoded with Specific Area Message Encoding.</p>
        </details>
        <details>
            <summary style="color:#FFFFFF;">Hint 2</summary>
            <p style="margin-left:1em; color:#FFFFFF;">The three buzzes are supposed to be identical, but in this challenge, they are different due to errors.</p>
        </details>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia;">
        </p>
    </span>
</div>

**Provided file: [warning.wav](https://2023.uiuc.tf/files/ff16d04bef6f15d6da26adab17478046/warning.wav)**

## 7. Corny kernel


## 8. Schrodinger's Cat ( after contest:< )

# OSINT

## 9. Finding Artifacts 1
<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
         <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        <p style="margin-left:1em; color:#FFFFFF;">
            David is on a trip to collect and document some of the world’s greatest artifacts. He is looking for a coveted bronze statue of the “Excellent One” in New York City. What museum is this located at? The flag format is the location name in lowercase, separated by underscores. For example: uiuctf{statue_of_liberty}
        </p>
        <details>
            <summary style="color:#FFFFFF;">Hint 1</summary>
            <p style="margin-left:1em; color:#FFFFFF;">The first two characters of the statue begin with "ma"</p>
        </details>
        <details>
            <summary style="color:#FFFFFF;">Hint 2</summary>
            <p style="margin-left:1em; color:#FFFFFF;">It is very prevalent in southern Asia</p>
        </details>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia;">
        </p>
    </span>
</div>



## 10. Finind Artinfacts 2
<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
         <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        <p style="margin-left:1em; color:#FFFFFF;">
            New York City is known for its sprawling subway system. However, none of that would have been possible without modern earth-moving equipment. Find where the first ever shovel was used to start digging the subway. Flag format should be in uiuctf{name_of_museum}
        </p>
        <details>
            <summary style="color:#FFFFFF;">Hint 1</summary>
            <p style="margin-left:1em; color:#FFFFFF;">well known for their baby blue colorings</p>
        </details>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia;">
        </p>
    </span>
</div>

## 11. What's for dinner

<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
         <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        <p style="margin-left:1em; color:#FFFFFF;">
            Jonah Explorer, world renowned, recently landed in the city of Chicago, so you fly there to try and catch him. He was spotted at a joyful Italian restaurant in West Loop. You miss him narrowly but find out that he uses a well known social network and and loves documenting his travels and reviewing his food. Find his online profile.
        </p>
        <details>
            <summary style="color:#FFFFFF;">Hint 1</summary>
            <p style="margin-left:1em; color:#FFFFFF;">what does joy translate to?</p>
        </details>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia;">
        </p>
    </span>
</div>


## 12. Finding Jonah
<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
         <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        <p style="margin-left:1em; color:#FFFFFF;">
            Jonah offered a reward to whoever can find out what hotel he is staying in. Based on the past information (chals), can you find out what the hotel he stayed at was? Flag should be uiuctf{hotel_name_inn}
        </p>
        <details>
            <summary style="color:#FFFFFF;">Hint 1</summary>
            <p style="margin-left:1em; color:#FFFFFF;">what does joy translate to?</p>
        </details>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia;">
        </p>
    </span>
</div>

**Provided file: [chicago.jpeg](https://2023.uiuc.tf/files/9c55eca8296b05baa372a345bb5acf87/chicago.jpeg)**

## 13. Jonah's Journal
<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
         <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        <p style="margin-left:1em; color:#FFFFFF;">
            After dinner, Jonah took notes into an online notebook and pushed his changes there. His usernames have been relatively consistent but what country is he going to next? Flag should be in format uiuctf{country_name}
        </p>
        <details>
            <summary style="color:#FFFFFF;">Hint 1</summary>
            <p style="margin-left:1em; color:#FFFFFF;">forks, trees, pushing, and pulling</p>
        </details>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia;">
        </p>
    </span>
</div>


## 14. First class mail
<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
         <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        <p style="margin-left:1em; color:#FFFFFF;">
            Jonah posted a picture online with random things on a table. Can you find out what zip code he is located in? Flag format should be uiuctf{zipcode}, ex: uiuctf{12345}.
        </p>
        <details>
            <summary style="color:#FFFFFF;">Hint 1</summary>
            <p style="margin-left:1em; color:#FFFFFF;">I think code is cool</p>
        </details>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia;">
        </p>
    </span>
</div>

**Provided file: [chal.jpg](https://2023.uiuc.tf/files/8f46e33bf590595eaf59163e6cd6b18f/chal.jpg)**

# REV ( after contest :< )
## 15. vmwhere1  
<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            Usage: <span style="color:red;">./chal program</span>
        </p>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia; color:#FFFFFF;">
        </p>
    </span>
</div>

**Provided files: [chal](https://2023.uiuc.tf/files/9c833de717949f0c01a8c2486d551825/chal) -- [program](https://2023.uiuc.tf/files/dfdb5cda5c5c875f4a73aa0b8d3ecbb8/program)**
## 16. vmwhere2
<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            Usage: <span style="color:red;">./chal program</span>
        </p>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia; color:#FFFFFF;">
        </p>
    </span>
</div>

**Provided files: [chal](https://2023.uiuc.tf/files/93c95d79b4734f30e9438158b3d19fc4/chal) -- [program](https://2023.uiuc.tf/files/0c928eeb2016c96a691f8848525b98da/program)**
## 17. geoguesser
<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            I thought geoguesser was too easy, so I made it harder.
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            Usage: janet -i program.jimage
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            nc geoguesser.chal.uiuc.tf 1337
        </p>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia; color:#FFFFFF;">
        </p>
    </span>
</div>

**Provided files: [janet](https://2023.uiuc.tf/files/f6aa81991db28950e07f800919c016e1/janet) -- [program.jimage](https://2023.uiuc.tf/files/a143ebe5eed56e3feba7826b2af729c0/program.jimage)**





## 18. Fast calculator

<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
           Check out our new super fast calculator!
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            This challenge is sponsored by Battelle.
        </p>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia; color:#FFFFFF;">
        </p>
    </span>
</div>

**Provided file: [calc](https://2023.uiuc.tf/files/3f98f9a2d482dbdf10f21f645d917214/calc)**

## 19. pwnykey



Link

<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
           Can you obtain a valid pwnyOS activation key?
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            [Link](https://pwnykey-web.chal.uiuc.tf/)
        </p>
        <p style="margin-bottom:1em; margin-right:1em; text-align:right; font-family:Georgia; color:#FFFFFF;">
        </p>
    </span>
</div>

**Provided file: [handout.tar.gz](https://2023.uiuc.tf/files/747bf836a19c58fac33518ad06a65e20/handout.tar.gz)**