---
layout: blog
title: Gleam
draft: false
date: 2025-05-01T12:00:00
date_updated: 2025-05-01T12:00:00
featured_image: /media/uploads/Screen%20Shot%202025-05-05%20at%2011.38.47.png
page_bg: oklch(0.76 0.13 25)
excerpt: Gleam is an AI-enabled mindfulness app which helps users to log things that have made them happy throughout the day, so that they can review and potentially find insights, recommendations or reassurance when things are overwhelming.
---
April's 'app of the month' is [Gleam](https://gleam.innes.hu). I often try to reflect on positive things that have happened to me throughout the day to try and place any negative experiences into the right context, and to give myself the opportunity to 'relive' a positive moment. There is some research which indicates that 'curating' memories and revisiting positive memories helps to reinforce them, so there are hopefully some benefits to this practice.

## Stuff I learned while I was building

- [Jazz](https://jazz.tools) was absolutely brilliant for taking this app from concept to reality. The main development effort for Jazz has been on React so far, but the Svelte stuff works, and there's some vanilla JS stuff that just works in the browser.
- This is my first AI-enabled app. It was absolutely child's play to do, and with Gemini's free allowance, users can bring their own key. I'd rather use an AI that doesn't train on submitted data as I think Gemini does, but this is a quick, free way to get something up and running.
- I spent some time with [Claude](https://claude.ai) on this one, mostly working on SVGs. I was very impressed with how well it could work, although I got a little frustrated with the limited conversation length, which meant I got two or three revisions before having to copy and paste everything so far and start again.

## My favourite feature

My favourite feature of the app is that you can **immediately** start using it. You don't have to register to use the app. All of your data will be saved locally until you register, and once you register, your data automatically flows into your new, registered account, and can be accessed from any device (assuming you have the passkey).

## My Favourite Piece of Code![](/media/uploads/carbon%285%29.svg)

This piece of code represents a simple feature which I spent quite some time thinking about. It creates a string of 'moment' IDs, and then hashes it. Then, it can be looked up in the list of summaries to see if you have already generated a summary which covers the exact same set of moments. I initially wanted to implement this based on days, but realised that I couldn't be certain that those days hadn't changed (had moments added or removed). There's a possible optimisation to be made here by using an object or a map to store the summaries, but for now, I don't think there's enough in it to make it worth optimising, especially as I think the more common use case is going to be iterating over the summaries to list them, so I will likely need the summaries as an array anyway (or iterate over the object/map), so this way is more memory efficient, and keeps things a bit simpler.

## What DIDN’T I build out/what are the next steps for this project?

So far, the list view for the generated summaries doesn't exist yet. I haven't worked out a perfect way to do it, and for now, it's probably not absolutely required. One other feature I'd have loved to have implemented, but which doesn't really exist at the moment is auto-generated summaries which are then sent to the user on a schedule (for example a weekly or monthly wrap-up). Unfortunately, there's no reliable way to do this without having a backend which fires push notifications, which adds complexity I'm not ready to build out just yet.

You can check out Gleam at https://gleam.innes.hu
