---
layout: post
title: Script to Download All Your Cloudinary Pictures
subtitle: Including All Metadata
tags: [bash]
---

The other day I was considering closing my Cloudinary account, so I decided it was time to get all my pictures. I guess I don't go much to their website, so I had not realized there is not a "Download All" button.

Well, I had to go and take a look at their API and wrote the script below, I hope it saves you a bit of time.

## What You Need

* Linux
* Git, curl, jq and awk
* Clone this BitBucker snippet and make it executable: [cloudinary_downloader.sh](https://bitbucket.org/snippets/jriano/4eboRR/cloudinary-downloader)

## What It Does

When you run it, it will create for you 2 directories:

* ~/uploads: Where your pictures will be saved
* ~/reports: Where json files will be saved. These json files have the pictures' metadata

## Configure It

Update the following lines in the script with your Cloudinary API credentials:

```bash
# Cloudinary credentials
c_account=youraccountid
c_api_key=yourapikey
c_api_secret=yourapisecret
```

## Run the Script

```bash
./cloudinary_downloader.sh
```

And wait a bit :)