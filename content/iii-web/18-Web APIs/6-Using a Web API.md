---
title: "Using a Web API"
weight: 30
pre: "6. "
---
{{% youtube 38AtVRSdYYE %}}

Finally, now that we've covered all of the aspects related to web APIs and how they are implemented, let's look at a quick example for how we can use a web API to interact with resources stored on the web.

## Finding an API

There are many great resources that can be used to locate a particular web API on the internet. Using search engines such as Google is one option, but there have also been many attempts to generate a directory of the most used and most useful web APIs such as the [Public APIs](https://github.com/public-apis/public-apis) project on GitHub.

There are also many scientific and research organizations that make their data available publicly via a web API. One of the most well-known is [NASA](https://api.nasa.gov/), which provides several APIs for developers to use. This includes everything from the [Astronomy Picture of the Day](https://apod.nasa.gov/apod/astropix.html) to information about the current [weather conditions on Mars](https://mars.nasa.gov/insight/weather/).

For this example, we'll use the [Astronomy Picture of the Day](https://apod.nasa.gov/apod/astropix.html) API. It is a very simple API - all we have to do is send a request to `https://api.nasa.gov/planetary/apod` and provide an API key. For testing, NASA provides the API key `DEMO_KEY` that can be used up to 30 times per hour and 50 times per day per IP address to test the APIs and explore what types of data they provide. So, we can use that.

### Making a Request

To make a request to the API, simply open a Linux terminal, such as the one in Codio, and enter the following command:

```bash
curl -X GET https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY
```

Alternatively, in most web browsers you can simply visit the url [https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY](https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY) to view the response in a browser. Since we are using a GET request, it is really simple to access.

### Viewing the Response

If done correctly, the API should send back a response formatted in JSON. The response itself may be just a blob of text, but if we reformat it a bit we can see that it has a simple structure:

```json
{
   "date":"2021-04-19",
   "explanation":"What does the center of our galaxy look like?  In visible light, the Milky Way's center is hidden by clouds of obscuring dust and gas. But in this stunning vista, the Spitzer Space Telescope's infrared cameras, penetrate much of the dust revealing the stars of the crowded galactic center region. A mosaic of many smaller snapshots, the detailed, false-color image shows older, cool stars in bluish hues. Red and brown glowing dust clouds are associated with young, hot stars in stellar nurseries. The very center of the Milky Way has recently been found capable of forming newborn stars. The galactic center lies some 26,700 light-years away, toward the constellation Sagittarius. At that distance, this picture spans about 900 light-years.",
   "hdurl":"https://apod.nasa.gov/apod/image/2104/GalacticCore_SpitzerSchmidt_6143.jpg",
   "media_type":"image",
   "service_version":"v1",
   "title":"The Galactic Center in Infrared",
   "url":"https://apod.nasa.gov/apod/image/2104/GalacticCore_SpitzerSchmidt_960.jpg"
}
```

As we can see, the API returned the picture for April 19th, 2021, along with the title, URL, and description of the image. So, if we make this request in an application, we can use the JSON response to download the image and display it, along with the title and description. That image is shown below.

![Astronomy Picture of the Day](apod.jpg)^[https://apod.nasa.gov/apod/ap210419.html]

It's really that simple! For more advanced APIs, we may have to include additional information in our request, as seen in the Twilio example earlier in this chapter, but, in general, using a RESTful web API is meant to be a simple and powerful way to interact with resources on the web.
