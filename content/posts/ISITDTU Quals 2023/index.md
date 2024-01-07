---
title: "ISITDTU Quals 2023"
description: "Writeup for ISITDTU Quals 2023"
summary: "Writeup for ISITDTU Quals 2023"
categories: ["Writeup"]
tags: ["Reverse","Misc","Top tier","CTF"]
#externalUrl: ""
date: 2023-12-20
draft: false
authors:
  - ryu
---


Hello, this is my Misc Writeups for ISITDTU Quals 2023. I have been waited for it since last year, but sadly, I was responsible for `Reverse` and `Misc` and I couldnt clear any of these 2 sections :< and this is the first time I played with a new team ( my brother's team ), so it was kinda interesting to talk about. Now, let's get started !!

# MISC
## 1. welcome
<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
8Q/2[6r[05G@bT,@o$rQ?Z[u/8Q0>FA9;s$@ru=2
<br>
            
</div>    
    
Used [cypher detect](https://www.dcode.fr/cipher-identifier) to find out which kind of encoding was, I saw that it used `ASCII-85` to encrypt the flag, now we just simply decode it and get the flag
    ![](https://hackmd.io/_uploads/BkYtOa3-T.png)
>flag: ISITDTU{wellcOme_t0_ISitdtu_ctf}
    
    
## 2. traffic

<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
I found a strange process on my computer trying to connect to the internet, can you tell me what it sends?
<br>
            <br>
Attachment: <a href="https://ctf.isitdtu.com/files/30c43f36255ce01b017d0670fb5bcf17/traffic.pcap?token=eyJ1c2VyX2lkIjoxMzAwLCJ0ZWFtX2lkIjo4NzksImZpbGVfaWQiOjI0fQ.ZS9FwA.kvYHcUGJxMpfc-iqQkPPXdH3cNY">traffic.pcap</a><br><br>
</div>    

Opened it with wireshark and exported the object in HTTP to see files sent and received, I saw that one sussy file here:
    ![](https://hackmd.io/_uploads/HysS563Z6.png)
After downloaded, I opened the file and had this:
    ![](https://hackmd.io/_uploads/H1wv9a3-6.png)
Looked like it was encrypted by something, but first we could see that`%3D` sussy in the end. Doing some research we would know that it is `URL encoding` and those`%3D` was just `=` symbol.
    
Fixing a little bit and we will have:
    ```O4ZWY3C7MQYG4M27NAZXEM27GFZV66JQOVZF6ZTMGRTQ====```
    
 now it looked like baseN encrypting, trying will multiple encrypting way and we see that it was Base32:
![](https://hackmd.io/_uploads/rkJM3ah-p.png)
    
>flag: ISITDTU{w3ll_d0n3_h3r3_1s_y0ur_fl4g}

## 2. Famous girl

<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            Cithrel Wynhice, a captivating social media influencer known for her beauty and wanderlust, had embarked on a journey to explore the enchanting landscapes of China. Her followers eagerly awaited her posts, hungry for the next breathtaking photo or exciting adventure. However, what started as a picturesque exploration soon turned into an unexpected mystery.
<br>
            <br>
Format flag: ISITDTU{f4k3_fL49}<br>
</div>     
    
At first, at any other challenges, I started at twitter but couldnt find anything helpful, so I headed to Insta and I had this:
    
 ![](https://hackmd.io/_uploads/Hy5OrT3Wp.png)
     
## 3. Famous girl

<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            Cithrel Wynhice, a captivating social media influencer known for her beauty and wanderlust, had embarked on a journey to explore the enchanting landscapes of China. Her followers eagerly awaited her posts, hungry for the next breathtaking photo or exciting adventure. However, what started as a picturesque exploration soon turned into an unexpected mystery.
<br>
            <br>
Format flag: ISITDTU{f4k3_fL49}<br>
</div>          
    
    
 ## 4. Discover

<div class="warning" style="padding:0.1em; background-color:#1A1F35;">
    <span>
        <p style="margin-top:1em; text-align:center;">
            <b><span style="color:#FFFFFF !important;"> Description</span></b>
        </p>
        <p style="margin-left:1em; color:#FFFFFF;">
            During her trip to China, Cithrel Wynhice posted a flycam-captured photo on her social media and challenged her fans to locate the exact spot in the picture and tell her the name of the tall building across from it.
<br>
            <br>
Format flag: ISITDTU{danang_azura_apartment}<br>
</div>          
    
    