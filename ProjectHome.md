"MJPG-streamer", is a command line application that copied JPG-frame from a single input plugin to multiple output plugins. It can be used to stream JPEG files over an IP-based network from the webcam to a viewer like Firefox, Cambozola, Videolanclient or even to a Windows Mobile device running the TCPMP-Player.
It was written for embedded devices with very limited ressources in terms of RAM and CPU. Its origin, the "uvc\_streamer" was written, because Linux-UVC compatible cameras directly produce JPEG-data, allowing fast and perfomant M-JPEG streams even from an embedded device running OpenWRT. The input module "input\_uvc.so" captures such JPG frames from a connected webcam.

This tool can be modified and distributed according to the terms of the GPL v2.

Currently no issues are known, but since this software is quite young and not used widely it may cause problems. You must really know what you are doing, if you use this software. If you want to use the software you are obliged to check if the sourcecode does what you expect it to do and take the risk yourself to use it.

To view the stream use VLC or Firefox and open the URL:
http://127.0.0.1:8080/?action=stream

To view a single JPEG just call:
http://127.0.0.1:8080/?action=snapshot

To compile and start the tool:
# tar xzvf mjpg-streamer.tgz
# cd mjpg-streamer
# make clean all
# export LD\_LIBRARY\_PATH=.
# ./mjpg\_streamer -o "output\_http.so -w ./www"

More examples can be found in the start.sh bash script.

In case of error:
  * the input plugin "input\_uvc.so" depends on libjpeg, make sure it is installed.

Dependencies for the input plugin "input\_uvc.so":
  * libjpeg
  * recent Linux-UVC driver (newer then [revision #170](https://code.google.com/p/mjpg-streamer/source/detail?r=#170))

Dependencies for the output plugin "output\_autofocus.so":
  * libmath