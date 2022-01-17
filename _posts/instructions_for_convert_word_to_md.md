### To create a md file use this code for GitHub:

* pandoc --extract-media=. -s 2022-01-16-Financial_Analysis-Excel_Basics.docx -t gfm -o mddoc.md
* Create a folder inside assets/images/ with the name of the article and Copy the media folder
* Change the name of the file with the location of the media file including
**/fastpages_3/assets/images/name-of-the-file/media**
* Copy this meta tag info and make changes

---
layout: post
title: Financial Analysis – Excel Basics
date: 2022-01-16 12:13:59.000000000 -04:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Financial Analysis
tags:
- Analytics
- Financial Analysis
- Business
meta:
author: Carlos Ordonez
permalink: /fastpages_3/financial%20analysis/2022/01/16/Financial-Analysis-Excel-Basics.html
excerpt: Basics of using excel for financial analysis .
---


After you press Enter, you’ll find you have a new file (name.md) containing your blog in markdown format, and a new folder called “media” containing a folder with the name of your doc. In that folder, you’ll find all your images. Use Explorer or Finder to move that folder into your blog repo’s images folder, and to move the markdown file name.md into your _posts folder.

You just have one more step. Open the markdown file in an editor or word processor, and do a search and replace (- in Microsoft Word), searching for “name/media”, and replace with “/images/name” (be careful to type the forward slash characters exactly as you see them). The lines containing your images should now look like this.

Us this link:
[https://blog.atwork.at/post/Convert-documents-with-Pandoc]
[https://www.fast.ai/2020/01/18/gitblog/]
