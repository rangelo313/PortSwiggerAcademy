Some applications allow users to upload files which are then processed server-side. Some common file formats use XML or contain XML subcomponents. Examples of XML-based formats are office document formats like DOCX and image formats like SVG.

For example, an application might allow users to upload images, and process or validate these on the server after they are uploaded. Even if the application expects to receive a format like PNG or JPEG, the image processing library that is being used might support SVG images. Since the SVG format uses XML, an attacker can submit a malicious SVG image and so reach hidden attack surface for XXE vulnerabilities.


This lab lets users attach avatars to comments and uses the Apache Batik library to process avatar image files.

To solve the lab, upload an image that displays the contents of the /etc/hostname file after processing. Then use the "Submit solution" button to submit the value of the server hostname.

The first thing I did is look up what this library does:
CVE-2015-0250
Found this payload accordingly and noticed that the user in this instance attempted to retrieve etc/passwd. 
<?xml version="1.0" standalone="yes"?><!DOCTYPE ernw [ <!ENTITY xxe SYSTEM "file:///etc/passwd" > ]><svg width="500px" height="100px" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"><text font-family="Verdana" font-size="16" x="10" y="40">&xxe;</text></svg> which results in a JPG file like this:

So I opened up the svg in vscode and added the payload above for the etc/hosts

After this I scrolled through the posts and did an inspect on the images and was able to determine that the output was correct.

Since it defines graphics in XML format then these files create a lot of attack scenarios like we can actually execute the XSS using the SVG file and can do a lot more. We can also execute XXE using these files which we are going to explore in this blog.

If application supports PNG, JPEG and other extension of file while uploading then there might be possibility that image processing library may support SVG files as they are graphics in format of the XML. Now our aim is to upload a malicious image that uses XML as a format with some of the XXE payload which actually fetches the /etc/hostname file if the file is processed.

Now you can see that the image file has been uploaded successfully now we have to check our avatar if it fetched or rendered any useful information.

Open the image in a new tab and you can actually see that it fetched the hostname of the server so we actually executed XXE by an SVG file on this system.


## Remediation:
1. If you are allowing user to upload image file on your server, whitelist the extension and don’t let them upload SVGfile.
2. If SVG files are business requirements then put a restrictions in place so that the command in those files doesn’t get processed.


Source:
https://gupta-bless.medium.com/exploitation-xml-external-entity-xxe-1f5f3e7bc5c4
