Published: https://medium.com/@bobvanluijt/google-s-answer-to-the-internet-of-things-ebd11b37f2ad

# Google’s Answer to the Internet of Things
*A bird’s–eye view on the business, design and technology side of Google’s proposition for the Internet of Things. These views are based on early access to Google’s Brillo and Weave developers platforms and the Ubiquity Conference held in January 2016 in San Francisco*.
## Pick Your Tool
In the early ’80s, the home entertainment industry rivalled over the Laserdisc and the VHS. For those in the industry, the answer was easy: the Laserdisc was far superior to the VHS tapes. Looking back on history, it is obvious that the VHS served customers much better - simply because it fitted what people needed at the time.
Today, at the dawn of a ubiquitous world, we can see a similar rivalry in the field of connected devices. Both collectives and organizations are trying to figure out how they can get a piece of the pie. Should it be a custom proprietary communications platform? A custom cloud solution? Or should it be an open source alternative that you could adopt and contribute to? What is the VHS of IoT? In this article, I am giving a bird’s–eye view of Google’s answer to this question: Weave and Brillo.
What are Weave and Brillo?
Weave, on top of Brillo or standalone, is an open communications protocol that you can use to connect devices in the cloud. Because of choices such as XMPP and mDNS, which clearly demonstrate well thought out user experience, Google is able to offer a full end-to-end solution for connected devices with Weave.
Brillo, also open source, consists of an OS (Android), core services, a developer kit, and a developer console. It is created to run on several development boards and microcomputers.

> Weave is at the heart of the two solutions, because it will allow you to create end-to-end Internet of Things products.

## Follow the Money
Last year (2015) was almost the year of the Internet of Things. Almost, because businesses are struggling to find the right monetization strategies and for the looks of it, traditional business models are being leveraged to fill those needs.

These propositions often consist of one or more of the four basic monetization options; devices, networks, APIs and/or cloud solutions.
The Device or The Firmware
Obviously, the creation of smart devices is one of the core monetizable options in this chain. Thanks to cheap microcomputers and microcontrollers smaller non-enterprise companies are able to compete in the connected market.
The API
How will the smart lighting installation inform the smart heating what its state is? The many possible protocols (Weave, eHomeKit, ZigBee, SmartThings and all custom built solutions) have their own ‘language’. A blue sky scenario would, of course, be an omnipresent protocol that all devices understand. Even though an open source solution like Google’s Weave seems an answer to this, we see more traditional enterprises starting to introduce proprietary APIs. And this is exactly the sticking point. If your whole organization is connected through an outsourced, governed API infrastructure, it might save you the trouble of going through the hustle of adopting an open source alternative. But practically, it also ties you directly to the owner of the proprietary language. The implications of this should not be underestimated. The smart grid, for example, is smart because it shares information. The detection of people in a room informs the lighting installation to switch on, but it also informs the heating systems to start working. Sharing of information is what makes the grid smart.
The Network
Monetization of the network is not new, but the fact that new open machine-to-machine equivalents are popping up like mushrooms is very interesting and might become a disruptive trend over time.
The Cloud
Under the pretext of more is better, data is being harvested from everywhere and the one who owns the most data seems to win the digital dollar. We see open cloud services (like Google with Weave) and proprietary, custom, private cloud services emerge as new cloud based business models.
Sharing of information is what makes the grid smart.
Google’s position
With Weave and Brillo, Google does what it always does: making the software so good that consumers basically want to give them their data. With an indirect monetization model, the cloud services connected to Weave are free. It seems like a win-win situation if you are in the IoT hardware business: you get top notch software plus a free cloud service. If you don’t mind having your product data in the Google cloud, you have everything you need to start building an IoT product.

## Google’s Design principles for IoT
The Internet of Things promises true ubiquity in our physical world. Designing the perfect machine interface for this promise will require tremendous creative design skills. Combined with the learnings of innovative software development and traditional design thinking we are looking towards brand new ways of designing the physical web. Although we can find more and more research and books on this topic, it still resides in the academic realm. The rise of (service) design in the technology sector seems a very promising development in the tech industry.
During the first Ubiquity Conference in San Francisco this year, Google introduced their vision on how a user should interact with their things in a ubiquitous world. These Design principles for IoT were built around the three concepts of being contextual, immediate and extensible.
A Dive into the Technology
With the three design principles and the four monetizable options in mind, we can start looking at software implementations and how Google’s Weave can help us succeed in creating an end-to-end connected product.

### 1. Brillo, Libweave and uWeave
Brillo is a stripped down Android version that can run on Linux kernel based devices. It does not contain things like a Java runtime, NDK, or Android Application Framework and runs on devices that have at least: ARMv7, Intel x86, or MIPS processor 32 MB RAM 128 MB flash storage or more.
— Weave on your Android devices.
Libweave is a C++ library that can be used on existing devices to integrate with Weave.
— Weave on your Linux kernel based devices.
uWeave (pronounced “micro weave”) is a stripped down version of Libweave aimed at microcontrollers.
— Weave on your microcontrollers.
One important question floating around the Internet is about the dependency of Brillo. Weave is not dependent on Brillo. You can use the C++ library Libweave or uWeave to connect your device to the Google cloud using the Weave protocol.

### 2. Connecting with HTTPS, XMPP and mDNS
Weave enables communication between the cloud and devices, and assumes your phone to be the ‘remote control’ of the devices.
Weave defines two types of APIs: cloud APIs and local APIs. The local APIs are created to ensure the immediate interaction with the device.

**HTTPS**
HTTPS is used for all device-to-cloud interactions. The Weave protocol is available trough the regular discovery channel.
note: currently the Weave protocol is not publicly available yet. As soon as Weave will be officially released, it will be available in the Discovery API.
— HTTPS to connected to the cloud.

**XMPP**
XMPP [wiki] is an XML-based messaging protocol used to create an immediate experience. 
— XMPP to create an immediate user experience.

**mDNS**
Multicast DNS resolves hostnames within a small local network without nameservers. [wiki]
— mDNS to create an immediate user experience.
### 3. Weave’s Cloud APIs
The Weave protocol is always used in combination with OAUTH and the registration of devices with a registration ticket.
Example of C++ Libweave integration
### Call:
Body POSTed to https://www.googleapis.com/weave/v1/commands
https://gist.github.com/bobvanluijt/7a529037170f10101e97#file-weave-example-call-json

### Action:
Chunk of the C++ action handling the request
https://gist.github.com/bobvanluijt/73e5e8b6cd95e8314ed0#file-exampl-chunk-libweave-cpp

Note:
At the time of writing, the Discovery API for Weave is not publicly available yet. As soon it will be available you can find it via:
GET https://www.googleapis.com/discovery/v1/apis/weave/v1/rest
4. Google Cloud and the Console

Devices are stored and managed in the Weave console. The console gives you the possibility to set up products and manage devices. Two notable options are the possibility to deploy updates on devices in badges and get anonymized device reporting.

## Conclusion
Although it is early days, it seems that with the Weave service and the Brillo platform, Google has created another top notch solution.
And as always, the interesting issue lies in the question: What’s in it for Google? And that is obviously the data in its cloud. But even without the Google Cloud, these solutions can be very useful. Because of the software completely being open sourced (including the soon to be released discovery API) it is doable to create an open-source or proprietary equivalent that can be used besides Google’s Weave cloud, something that would be ideal for companies who want to store their data in their own cloud solution.
Whatever direction you will take for your solution (Weave in the Google Cloud or Weave with a custom cloud), it will be a win-win situation for Google- because these two opportunities seem to be likely candidates to become the VHS of the Internet of Things.
