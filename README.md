# libwebcam
## Lightweigh C++ webcam library

### What is does
Provides access to your USB webcam using object oriented aproach. 

### Main features:
* Image acquisition
* Webcam enumeration
* C++ 11 compliance
* Portablity (Windows, Linux)
* Built on top of Video4linux (Linux) and DirectShow (Windows)
* Ease of use

Usage example:
```c++
...
#include <libwebcam/webcam.h>
...
int main()
{
    try{
        webcam::video_settings video_settings;
		video_settings.set_format(webcam::format_JPEG());
		video_settings.set_fps(6);
		video_settings.set_resolution(webcam::resolution(320, 240));
		
		unsigned char device_number = 1;
		webcam::device device(device_number, video_settings);
		device.open();
		for(int i=0; i<100; i++){
		    webcam::image * image = device.read();
		    //do somethig with image
		    delete image;
		}
		device.close();
    }
    catch (const webcam::webcam_exception & exc_){
		std::cout<<exc_.what()<<std::endl;
	}
	return 0;
}
```
### How to use libwebcam
* Install source using [installation guide]
* Include header `#include <libwebcam/webcam.h>`
* Enumerate for available webcams
* Setup webcam::video_settings using enumerated video parameters
* Create instance of webcam::device passing number of device and video_settings (number starts from 1)
* Open device, read images, close device

You can also find usage examples in libwebcam/examples directory 

### License
MIT © [Robert Andrzejczyk]
# TODO
### Contribute
Contributions are always welcome!
### Contact

[installation guide]: http://rojarand.github.io/libwebcam
[Robert Andrzejczyk]: https://github.com/rojarand
