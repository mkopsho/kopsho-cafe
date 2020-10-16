# Building a (good!) Twitterbot with Python
## Prettifying your Twitter timeline, one bot at a time
#### October 2020

## 2020: A Terrible Robot Future
![terminator.gif](../../images/twitter_bot/terminator.gif)

Twitter is chock full of [bots](https://www.cnbc.com/2017/03/10/nearly-48-million-twitter-accounts-could-be-bots-says-study.html). A huge portion of Twitterbots are seemingly meant to amplify terrible political takes and spam your timeline with a bunch of weird nonsense.

But it's not all bad. There are some diamonds in the rough:
- [@PossumEveryHour](https://twitter.com/PossumEveryHour)
- [@WITCHES_WIZARDS](https://twitter.com/WITCHES_WIZARDS)
- [@Clipart1994bot](https://twitter.com/Clipart1994bot)

All of these do one thing and one thing well: post cute, funny, and/or interesting pictures to Twitter. If you follow these handles, chances are you will turn your timeline from a miserable blood-quickening experience to more of a chill, benign one. Which we could all use more of, I think. More of *these* bots, less of *those*, please!

I've been meaning to learn Python for awhile and I thought that this would be a good way to do it. My final React project for my bootcamp, called [STWRDSHP](../flatiron/react-conventions-and-stewardship.html), took data from the National Park Services API and fleshed out a nice looking site with parks that you could favorite and add to lists.

## Ay-pee-eyes! Ay-pee-eyes!
Since I already knew how the NPS API was laid out, my main challenge was to figure out how to access and use the Twitter API. Luckily, [applying for a developer account](https://developer.twitter.com/en/apply-for-access) is very easy and was approved within a few hours. Python, much like Ruby and JavaScript, has a [robust package ecosystem](https://pypi.org/) that I used to find a [lightweight wrapper](https://github.com/geduldig/TwitterAPI) for the Twitter API. Interacting with the Twitter API at this point was a simple matter of following instructions in the README and familiarizing myself with the popular [requests package](https://requests.readthedocs.io/en/master/).

## What to post?
![zion](../../images/twitter_bot/zion.jpg)

I essentially wanted this bot to do one thing:
1. Tweet a national park every couple of hours.

In order to do that, these steps would need to occur:
1. Fetch a random park from the NPS API.
2. Fetch a random image from that park's collection of images.
3. While fetching an image, grab the park name and NPS website, as well.
4. Post this data to Twitter via their API.

When uploading media, Twitter requires that you upload the media file(s) first:
```
## Upload image
def upload():
  image_path = "IMAGE_PATH"
  if os.path.getsize(image_path) <= 5242880:
    file = open(image_path, 'rb')
    data = file.read()
    request = twitter_api.request('media/upload', None, { 'media': data })
    print("Success" if request.status_code == 200 else "Failure: " + request.text)
    reference(request)
  elif os.path.getsize(image_path) > 5242880:
    download()
```
...then reference the *media_id* from the response when actually posting your tweet. This second call includes the text of the tweet (fetched from the NPS API in an earlier method):
```
## Reference uploaded image and tweet
def reference(request):
  if request.status_code == 200:
    media_id = request.json()['media_id']
    request = twitter_api.request('statuses/update', { 'status': park_stats["full_name"] + " | " + park_stats["website"], 'media_ids': media_id })
    print("Success" if request.status_code == 200 else "Failure: " + request.text)
  # Cleanup
  if os.path.exists("IMAGE_PATH"):
    os.remove("IMAGE_PATH")
  else:
    print("The file does not exist")
```
We also clean up the image that we save so that we start afresh next run.

## Scheduling
Since I'm using a Mac, I opted for `launchd`, which is its version of `cron`:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>michaelkopsho.twit</string>
    <key>ProgramArguments</key>
    <array>
        <string>/Users/michaelkopsho/.pyenv/shims/python3</string>
        <string>/Users/michaelkopsho/learning/twit.py</string>
    </array>
    <key>StartInterval</key>
    <integer>7200</integer>
    <key>StandardOutPath</key>
    <string>/Users/michaelkopsho/out.log</string>
    <key>StandardErrorPath</key>
    <string>/Users/michaelkopsho/error.log</string>
</dict>
</plist>
```
I log errors and output to two log files so that I can tail them and see what's happening if my program ever horks. `launchd` has obvious limitations, namely, that it won't run if my laptop is ever asleep or off. A good fix for this would be running this in a Droplet, a Pi, or some of those newfangled serverless functions that folks seem so excited about these days.

## [It lives!](https://twitter.com/natl_park_pics)
![Frankenshteen!](../../images/twitter_bot/frankenshteen.gif)

The code for this is [very small (~60 lines)](https://github.com/mkopsho/natl_park_pics_twitterbot) but it gets the job done and, I believe, gets it done well!

Overall, this was a fun little project to start cutting my teeth on procedural Python. Python feels a lot like Ruby with some minor differences, at least in this context. I'm sure that I'll observe more differences the more I use either language!

Happy tweeting!

[⟵   back to blog](./blog-home.html)
