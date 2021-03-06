How to use this app
===================

This app shows mjpeg (also known as webcam) streams. Type the URL of your mjepg-stream in the URL-box and choose connect. 
A lot of streams can be found here: http://www.mjpeg.net.

These examples worked the last time I checked:

URL: http://82.147.33.166/mjpg/video.mjpg?camera=1
URL: http://87.213.108.6/mjpg/video.mjpg?camera=1

Enter these URL's in the URL-box of the Webcam Pi app and leave the uername and password blank.

Setup your OWN MJPEG stream
===========================

To install a webcam streamer on Windows, download webcamXP at http://www.webcamxp.com/home.aspx and install.
The standard URL of your WebcamXP stream is http://IPADDRESS/cam_[CHANNEL].cgi.

To setup your own MJPEG stream from a Raspberry (small computer) or LINUX computer, follow the following steps.

PiCam-Setup
===========

A simple install script for initializing your Raspberry Pi with mpeg-streamer to stream your webcam on a Raspberry PI.
To run the script make sure your repository is up-to-date and Git and dialog is installed. 

```
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install -y git
```

After this you can download the script

```
cd
git clone git://github.com/Ploeper/PiCam-Setup.git
```

Execute the script

```
cd PiCam-Setup
sudo chmod +x picam_setup.sh
sudo ./picam_setup.sh
```

After the installation you can run the picam_run.sh script to launch the webcam with some default example options.

```
sudo chmod +x picam_run.sh
sudo ./picam_run.sh
```

To launch the webcam streamer with the parameters for your webcam, edit the picam_run.sh script. To launch the webcam on boot with
your parameters, edit the picam_service.sh script and launch the boot option in the setup script.

# Access your webcam
Get the IP adress of your Raspberry

```
ifconfig
```

The eth0 interface should display your IP-adress. Type 'your-ip:8081' in your address bar and you should see the webserver of mpjg-streamer.

# Internet access/Webcam Pi
To access the webcam through Webcam Pi, you must forward your router. There are a lot of tutorials on this topic (http://www.wikihow.com/Set-up-Port-Forwarding-on-a-Router).
The default port is 8081 and you should forward this to the Raspberry Pi device.

## Security
To secure your webcam, add the following parameter to your launch-script

```
mpeg-streamer ... -c username:password
```

Don't forget to rerun picam_setup.sh if you edited the picam_service.sh file.

## Windows Phone App access
In the URL field of the app type 'http://ip:port/?action=stream. Leave the username and password field blank if you have no security settings.

# Stop

To stop the webcam streamer run

```
killall mpjg_streamer
```

