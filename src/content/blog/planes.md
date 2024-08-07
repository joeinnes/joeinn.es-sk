---
layout: blog
title: Planes ✈️
draft: false
date: 2024-06-06T15:22
date_updated: 2024-06-06T15:22
featured_image: /media/uploads/Planes iPhone SE.png
page_bg: "#fa646a"
excerpt: I wrote yet another web app which is a semi-augmented reality type app for identifying planes which fly across in front of my balcony.
---
So, a couple of months ago, we (sort of by surprise) moved flat. We found a lovely flat up in the hills on the Buda side with a view out over the city, space, and a lovely green garden. One of the best features of this flat though is the balcony. It has a small but adequately-sized balcony for a three person family which looks out over one of the main flight paths into Budapest airport (the runways are 13/31, with the 130° direction seeming to be preferred during the day).

So I see all these aeroplanes flying low and close to my balcony, and I look at the tail to see if I can guess which airline they're with. FlightRadar24 is amazing and shows plane movements in real time, so I was using that, but sometimes it's a bit tricky to get it to load, zoom in, especially on mobile.

I thought 'hey, wouldn't it be great to have this in an app where I can just point my phone off my balcony and tap on the plane?'

So I started building.

## Problem 1: Data

So I looked into it, and the FlightRadar24 API is something that you either need to pay for, or you need to contact them or something, and I couldn't be bothered with that. I found [this blog](https://jacobbartlett.substack.com/p/my-toddler-loves-planes-so-i-built) which actually is very close to the problem I was also trying to solve, and it talked about using the 'OpenSky Network API', but when I went to sign up for a key, there was a big warning that they couldn't process new registrations for 'a few days'. This was about six weeks ago and the message is still there, so I guess they're finding it harder than they thought they would.

Eventually I settled on a provider called 'airplanes.live', which I doubt will be around forever, but works for now. I could just grab the longitude and latitude of the user, and pass that to a fetch query with a small radius (I settled on 30nm).

## Problem 2: Device Info

Great, so now I've got a list of all the planes within 30nm of my user's location. I filter them quickly for ones which are on the ground, and then I'm left with ones that the user could potentially see.

So now I need to work out how to get the user's device orientation. I decided (perhaps simplisticly) that I only care about the *heading* of the user's device, and that I'll just have a div 80% of the viewport represent everything from the horizon to the zenith. I added a quick green div (20% of the viewport) underneath the top bit to simulate a horizon. No, it's not topographically correct, but who cares.

This can only be enabled interactively, so I stuck a big button for users to click to start the heading tracking, and we're off to the races. Now all I needed to do was calculate the bearing to each aircraft based on my lat/lon and the aircraft's lat/lon, and exclude any which are more than ±90° to exclude those in the opposite direction to the direction I'm looking, then calculate what percentage of the way through my theoretical 180° 'window' the bearing is, and draw the plane there.

## Problem 3: Altitude

So, altitude sent me back to secondary school maths. I have the altitude of the aircraft, and I can calculate the distance to the aircraft, meaning I have the *adjacent* and the *opposite* sides of the right-angled triangle which represents me looking at the plane and the ground.

SOH CAH TOA to the rescue. I know that I can calculate the tangent of the angle by dividing the opposite (altitude) by the adjacent (distance). Then I can use the `atan` function to calculate the angle itself. Now I've got the angle, and I know that directly above me is 90°. So if the angle is 45°, then I can just render it 50% of the way up the div. Yes, it's not perfect, but works pretty well.

I added a few other things, like scaling the plane icon based on distance and flipping it based on the plane's heading, etc., and launched it at https://planes.innes.hu.

Best used on a mobile, rough around the edges.

![App](https://joeinn.es/media/uploads/Planes%20iPhone%20SE.png)
