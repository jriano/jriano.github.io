---
layout: post
title: This Is How I Backup My Pictures and Videos
subtitle: And My Wife's and Kids' and Mother in Law's
tags: [bash]
---

About 6 years ago I was moving pics out of my cellphone. When I finished, I deleted some of the folders and I moved others around. Today I still feel chills, those chills I felt when I realized I had deleted the wrong folder, and because I moved folders around I ended up overwritting hundreds of pictures that were gone for ever!

After that, I started using tools to backup my pictures, but eventually I ended up writing these scripts to do it the way I want it. So if you have a Linux box, let me show you how they work, and may be you will be spared from losing some of your precious pictures.

## What You Need

* Linux, with the following installed
* Git, grep, awk, rsync, exif, jq, stat, file
* Clone this repo: [bitbucket.org/jriano/backup-media](https://bitbucket.org/jriano/backup-media)

## What It Does

When you set a **source** location, the scripts recursively search there for videos, pictures and voice recordings, and moves them into a *pictures*, *videos* and *audios* directories sorting them by year-month. If the files don't have the appropriate metadata, they are stored in a **no-date** folder.

## Configure It

In the repo there is a file named **dirs-sample.json**, make a copy of it and name it **dirs.json**. The file has the following contents:

{% highlight json linenos %}
{
    "source": "/home/juan/Pictures",
    "picsdestination": "/media/juan/T2/Family-Pictures",
    "vidsdestination": "/media/juan/T2/Family-Videos",
    "audiosdestination": "/media/juan/T2/Family-Audios",
    "prime": "/media/juan/T2/Prime-Pictures"
}
{% endhighlight %}

Edit the files to match your folder structure.

**source** is the single place where you dump your media to be sorted. The following 3 directories are the destinations for each kind of media. **prime** is still not used, I intend this to be a location for your best pictures.

## Run the Script

```bash
./backup_media.sh
```
The script will move the files to the new locations. The final result should be something like this:

```bash
juan@laptop:/media/juan/t2/family-pictures$ ls | head
2005-01
2005-02
2005-03
2005-04
2005-05
2005-06
2005-07
2005-09
2005-12
2006-02
```

## That's All Folks!

You may run into some file types not being recognized, if that's the case let me know. Also, don't worry about overwritting, as the script compares with md5 and rename files if two have the same name and are not the same file.