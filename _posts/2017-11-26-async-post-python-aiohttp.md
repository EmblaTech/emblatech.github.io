---
layout: post
title: "Async POST requests in Python with aiohttp"
quote: "I was f☆☆☆ed at one point that being a Python 2.X developer for ages, and now had to develop a truly asynchronous http post request script to upload files to a third party service in a day. IN A FREAKING DAY!"
image:
      url: /media/2017-11-26-async-post-python-aiohttp/nasa-53884-unsplash.jpg
video: false
comments: true
author_name: Chathuranga Bandara
author_url: https://chathuranga.com/
author_pic: chathuranga.jpg
---

<p>
	<small class="_1l8RX _1ByhS"><center>Photo by <a href="https://unsplash.com/photos/Q1p7bh3SHj8?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">NASA</a> on <a href="/search/photos/network?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></center></small>
</p>

<style type="text/css">
  #post-info h2 {
      background-color: rgba(0,0,0,.5);
        padding: 10px;
  }
</style>

I was f☆☆☆ed at one point that being a Python 2.X developer for ages, and now had to develop a truly asynchronous http post request script to upload files to a third party service in a day. IN A FREAKING DAY!. Okay I might have been doing too much caffeine and other stuff that my heart started to pump more than usual, but I needed to prove myself and others that I’m a bloody Python guru.

Anyways, I searched the web, the God Almighty Stackoverflow and the sexy chick who may or may not got herpes Medium among others hookers and dolls of technology blogs and gists yet could not find an understandable or rather useful way to do it. So i was back to square 1. Among the prayers to the Gods of Python, reading the Zen of python loud, sacrificing the morning coffee to the Guardians of multidimensional programming languages, I wished I was born in another realm where people spoke in Python. However, Unless I’m Harry Potter I would not be able to understand the snake language hence, I had to search all in English.

Yes, I’m bit deviating from the point! Anyways, What I had to do was change a synchronous rest post call which uploads all the files in a folder to a third party service and make it go asynchronous. The reason being, Synchronous one actually required 10 minutes + to upload the files and being this a part of the deployment process, that did not made my Product Owner very Happy.

~~~python
import requests
import argparse
import os
parser = argparse.ArgumentParser(description='Build Script')
parser.add_argument('-host', help="url host of the site")
parser.add_argument('-folder', help="folder which needs to be updated")
parser.add_argument('-app_id', help="app id")
parser.add_argument('-token', help="app external token")
args = vars(parser.parse_args())
for path, subddir, files in os.walk(args['folder']):
   for f_name in files:
       file_url = os.path.join(path, f_name)
       url = 'https://app.website.io/upload/jssymbols/'+  args['app_id'] +'?authToken=' + args['token']
       r = requests.post(url, data ={
            url: file_url
           }, files={'file': open(file_url, 'rb')})
~~~

Simple stuff. Then I had to write this asynchronously and requests library being a sassy little bi☆☆h, I had to find a macho library to do this. I knew that I had to use asyncio which is built in in Python 3.5 and between couple of libraries I picked aiohttp, which have a very good documentation. The Idea was simple, I had to use a threadpool and send async requests which runs until the files are done. However, since a new TCP open with each of the request is costly, understood that I had to use some kind of a session open.

The keywords here are async, await, loop and session. First lets take a look at the code and then try to comprehend what it does.

~~~python
import asyncio
import aiohttp
import argparse
import os
parser = argparse.ArgumentParser(description='Build Script for RayGun')
parser.add_argument('-host', help="url host of the site")
parser.add_argument('-folder', help="folder which needs to be updated")
parser.add_argument('-url', help="raygun url")
args = vars(parser.parse_args())
async def send_file(path, f_name):
   file_url = os.path.join(path, f_name)
   url = args['url']
   async with aiohttp.ClientSession() as session:
      _url = args['host'] + file_url[2:]
      print (_url.replace('\\','/'))
      async with  session.post(url, data ={
            'url': _url.replace('\\','/'),
            'file': open(file_url, 'rb')
      }) as response:
            data = await response.text()
            print (data)
futures = []
for path, subddir, files in os.walk(args['folder']):
     for f_name in files:
           futures.append(send_file(path, f_name))
loop = asyncio.get_event_loop()
loop.run_until_complete(asyncio.wait(futures))
~~~

First I had to decouple sending one file with the foreach where sending one file is the one which should be async hence the “async” keyword. And then I had to use the session “async with aiohttp.ClientSession() as session” says that I had to use the session which comes with aiohttp and make it work as async which returns a response which is also async hence I have to “await” the response which then printed out once its resolved.

Futures is a cool way of handling async calls in asyncio library. It takes a list of functions which needs to be awaited and run async which then gets to an event loop which uses “runs_until_complete”to run until all results were resolved. (If you want you can use “run_forever” as well if you fancy being intimate with your performance)

However, there you go. Use this, and modify it and make sure you also pray for my forthcoming pains since Python 2.7 is done in a month or so (from Dec 2017). All hail the Giant Snake.
