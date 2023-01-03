Two fundamental building blocks in the Volkswagen Automotive Cloud are **Vehicles** and their **Devices**.

Every developer interaction starts with a vehicle. And every vehicle includes on-board devices that manage the "command and control" of the vehicle's numerous sensors, actuators, and motors.

Understanding vehicles and devices is a prerequisite for any successful interaction with a **Connected Vehicle** including:

- Sending commands to a vehicle
- Retrieving telemetry from a vehicle
- Analyzing data about a vehicle


## Legacy Vehicles vs. Connected Vehicles

A **legacy vehicle**, from the perspective of the VW.AC Platform, is any vehicle that includes devices which, though they may be able to respond to remote commands and gather telemetry data, they cannot be configured to communicate *directly* with the VW.AC Platform (though these vehicles and their devices might communicate to *other* Internet-based platforms). 

**Note:** In order for a **Legacy Vehicle** to connect to VW.AC, an intermediary service, such as a Hybrid Architecture Custom Cloud Gateway (CCG), would be needed to intercept the communications between the legacy vehicle and its original data platform. Such an intermediary service could be used to enable sending of commands from VW.AC to the vehicle and for telemetry uploaded by the vehicle to be captured and mirrored into the VW.AC Platform.

A **Connected Vehicle**, as defined by VW.AC, is any vehicle that contains one (or more) on-board devices which are able to communicate *directly* with the VW.AC Platform. These "smart devices" generally are configured to run an "automotive edge" runtime software environment.


## In-Vehicle Devices

Modern vehicles contain an ever-growing number of sensors, actuators, motors, and Electronic Control Units (ECUs).

One electronic control unit could be connected to and manage all the motors, features, and sensors for the driver's side window. Window features might include "auto-up" and "auto-down" capabilities, and pressure sensors might be used to detect when objects are in the way (such as an arm) and prevent injury.

Another ECU could be in charge of the climate control systems and manage temperature sensors, heating, cooling, and fans. Yet another ECU could manage the rain sensors and automate the windshield wiper motors. These purpose-specific, or zone-based, ECUs are often low-end to mid-range computing devices (such as an HCP1, HCP2, or HCP3) while a **Central ECU** is usually a more powerful HCP5 (High-performance Computing Platform 5) or an In-Car Application Server (ICAS).

### An HCP5 ECU device<sup>1</sup>
<img src="../images/training4.0/HCP_ZF_ProAI_02.png" alt="HCP5" /> 

### Central ECU
The main, or Central ECU, is responsible for managing the in-car communication between the numerous zone-based ECUs distributed throughout the vehicle via a Car Area Network (CANBUS). It is also tasked with communicating to a cloud platform, like the Volkswagen Automotive Cloud, via a wireless Internet connection controlled through a Connection (or communications) Module (ConMod). The Central ECU also has access to a Hardware Security Module (HSM) that is used to manage the encryption and decryption of messages to and from the cloud platform.

In current-generation vehicles, it is common for only the Central ECU (often an HCP5), and possibly the in-vehicle infotainment system's ECU (often an HCP3 and referred to as the "IVIDevice"), to be registered with the VW.AC cloud.

<img src="../images/training4.0/Full-Connected-Vehicle-07b.png" alt="Connected Vehicle" />

As vehicles advance and devices get smarter and faster, it is likely that more and more devices will be registered in the VW.AC Platform for each vehicle. It is also possible to register numerous devices for a given vehicle in VW.AC as a means of creating a complete catalogue of device details, hardware, firmware, features and capabilities to be leveraged by the business logic of a development partner's application or service.


## Vehicle and Device Registration

When working with an actual vehicle, the vehicle would have already had its Central ECU and infotainment ECU pre-installed while still on the production line. In some instances, the vehicle may have already been registered to the VW.AC Platform. If not, or if you are still in the testing and development stages, you may need to perform the vehicle registration yourself.

- See the tutorial: [Define & Configure > Register a Vehicle](/s/document-item?bundleId=vwac-documentation&topicId=training4.0%2FTry-it-01-Register-a-Vehicle.html)

Similarly, the device(s) installed in those actual vehicles may have already been registered to the VW.AC Platform. If pre-registered, those devices would have already been loaded with the necessary authentication certificates and associated with their vehicle in the VW.AC Platform. If not, you will need to perform the registration process for the devices yourself and associate them with your vehicle.

- See the tutorial: [Define & Configure > Add a Device](/s/document-item?bundleId=vwac-documentation&topicId=training4.0%2FTry-it-02-Add-a-Device.html)


## Adding Devices

You can register (add) a device to a vehicle in the VW.AC Platform in two ways:

- As part of the **Register Vehicle** API operation
- Via the **Add Device** API operation

Both methods are equally valid and produce identical results. Registering a vehicle and adding a device in a single **Register Vehicle** API request is slightly more efficient; but registering a vehicle by itself in the first API call and adding a device in a subsequent **Add Device** API request provides a cleaner audit trail, is easier to troubleshoot, and may be simpler for others to follow your code's logic.


## Device Authentication

For security reasons, any device that attempts to communicate with the VW.AC Platform must be authenticated and the communication must be encrypted.

This authentication and encryption is done using X.509 certificates signed by the Volkswagen Certificate Authority (CA).


#### Endnotes

<sup>1</sup> Image source: [NVIDIA ProAI ZF](https://nvidianews.nvidia.com/news/volkswagen-and-nvidia-to-infuse-ai-into-future-vehicle-lineup)