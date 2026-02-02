---
title: "Building a poster generator for live concert videos"
date: 2026-02-01
---

I enjoy watching concert streams, however its difficult to keep track of whats out there when its spread between Youtube, private short lived links and services such as nugs. I just locally download ones I'm interested in and feed them into a library in Plex called "Concerts". 

The difficulty comes in the metadata, for nearly all of them they have no entry in any of the online metadata libraries and even if they do there is almost never artwork. I can easily populate the metadata but its common for there to be no poster from the band or festival so I have a proper title and release date but no poster. Plex will display a random thumbnail from the video as the poster which looks bad and typically gives zero indication of what the content is. 

I had played around with generating artwork using AI but had issues with consistency and text generation. They would either be in the uncanny valley or have that general AI look which I didnt like.  

*I wanted a way to easily generate posters from a frame of a video and then overlay text ontop.*

I have experience using the Python library Pillow for image manipulation and knew generally the approach I wanted to take. I figured this was a good oppurtunity to use Claude Code desktop app, so I signed up for the Pro Plan. 


My first prompt was a basic spec 

```
I want to make an app that will let a user generate plex posters from videos with them selecting the frame from a video or background color and then overlaying text overtop

Workflow

1. Pick a video file
2. Breakdown the video file into images, it should only generate lower quality images for this initial selection to help speed up the process and save on the temporary storage it would consume. the actual poster generated should use the highest quality though
3. Display the images with a slider allowing the user to run through all images
4. It should display a overlay that displays what the poster would contain as the video files will be widescreen and the poster will be a 2:3 aspect ratio, this overlay can be moved around and the image can be zoomed in
a toggle for image/colour background will let users switch between using an image from the video or just colour options. It can either be a single colour or a 2 colour gradient
5. After selecting the background image/colour it now allows the user to insert text, there can be multiple text boxes and they can be moved around freely, a few basic font options and formatting options should be available (bold, underline)
6. User clicks on generate and poster is saved to the output path


Deployment: docker
runtime: python

Dockerfile
minimal image

docker compose
path for video files (can be multiple)
path for generated posters
port for webui

I've included an example of a basic black backgrounded poster.

ive also included a basic mock of the UI
```

My drawing skills are essentially zero, please excuse what was supposed to be a stick figure shooting a cowboy that looks more like a old defenseless woman being shot. 

![hand it over you old biddy!]({{ site.baseurl }}/assets/images/2026-02-01-generate_posters/ui_mock.png)

Depending on how much success I have with more instances of this I may pivot to some WYSIWYG tool so the LLM has a better chance of interpreting what I want but theres something nice about quickly drawing it on the iPad in 2 minutes.

Claude then asked some clarifying info, ill note that Claude doesnt seem to have a good way to either export out this workflow nor does it let me view these questions after the fact 

![]({{ site.baseurl }}/assets/images/2026-02-01-generate_posters/claude_missing.png)

