# General mechanism
A local OVL portal is available on board the ship. It runs on ODL server, and is reachable using the Science or the C Networks. 

The main advantage to this local portal compared to the online https://ovl.oceandatalab.com portal is to limit internet consumption and provide an offline access to data. 
Using a specific range of IP, you can connect to the server, browse the data of interest that will be stored in the cache. Any other user will use the already downloaded data. 
Only authorized people (using specific IPs) will be able to download new data. All the other users will only have access to already downloaded images

Depending on what you want to do, you will need to connect to different networks.

# Update local OVL portal content

Before accessing C-Net with unlimited internet access, turn off all synchronisation, if possible configure your device in `Data saver mode`. In any case, monitor the network carefullyto ensure that you have full control of your data consumption.

## Connect your computer on the C-Net network, 
You can connect either using the properly labeled cable in the wetlab, or using the WIFI in the classroom:
	- C-Net WiFi Name: `Teachers-WiFi`
Ask Natacha or Lucie for the Password

Check that your IP address is in the range 10.22.0.*

## Connect to local OVL portal on C-Net

Open the following address in your web browser of choice:
- [http://10.22.0.19](http://10.22.0.19)

The OVL portal should open and you should be able to load new data. You should see a button with a cloud icon on the right in the title bar of the OVL portal. Its color indicates:
* Blue: You are using the online servers and updating the local cache
* Grey: You are using the local cache

Click that button to change its color.

Any data loaded when using this portal will be cached automatically and will be accessible by the students. Be sure to browse data at the resolution of interest to load the necessary content. 
For example you can select all your data of interest and zoom in and out to load different resolution. Even if the selected data are in a layer hidden by the other ones, it will be loaded.

Open the following address in your web browser of choice to verify that the datahave been properly cached using the following address (you will not be able to update the local cache using this address):
- [http://10.22.0.19/student.html](http://10.22.0.19/student.html)

# Browse already Downloaded data
I would suggest to connect to the Science Network (S-Net) when you don't need to download additional data to limit your data connection

## Connect your computer on the S-Net network, 
You can connect either using the properly labeled cable in the wetlab, or using the WIFI in the classroom:
* WiFi Name: `WiFi - Class - Banjer`
* WiFi Password: `OneOceanExpedition!`

Check that your IP address is in the range 192.168.3.*

## Connect to local OVL portal on S-Net
Open the following address in your web browser of choice:

- [http://192.168.3.117](http://192.168.3.117)

The OVL portal should open with all data that has been preloaded by one of the
 lecturers. Using this address you cannot update the local cache so if you need additional data, ask someone who has access to the C-Net. 