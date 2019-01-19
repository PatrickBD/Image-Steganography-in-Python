# Image-Steganography-in-Python

Image Steganography: Hiding images, text files, and other data inside of images.

## Hiding Star Wars in Images

Steganography is the practice of concealing a file, message, image, or video within another file, message, image, or video. Whereas cryptography is the practice of protecting the contents of a message alone, steganography is concerned with concealing the fact that a secret message is being sent as well as concealing the contents of the message. (https://en.wikipedia.org/wiki/Steganography) This notebook will use least significant bit steganography to hide 100s of KB to several MB of data in an image without perceptibly changing the image. This is my attempt to duplicate the method without looking up tutorials or code samples on least significant bit steganography. My only knowledge going into this is a basic description of the method.

### Least Significant Bit Image Steganography Explained

Here is a quick rundown of how this works. Each pixel in a color image has a value for each of it's 3 color channel. These values are between 0 and 255 corresponding to how red, green, or blue that pixel is. These values can be converted to an 8 bit binary value (255 = 11111111, ect.). While changing the left-most bits can mean a lot of change to the value, the rightmost bits mean very little. We are going use the rightmost 2 bits for our encoding. Changing these 2 bits will change the value for that one color channel on that one pixel by at most 3 points but more likely less or not at all. The result is a difference in the final image that is imperceptible to the human eye. If we are willing to replace these 2 bits of the 8 bit value, we can use up to 1/4th of the image's total space for whatever else we want! If we convert our scripts to 8 bit binary as well, there is more than enough space in a single color image to replace the last 2 bits of each color channel with our scripts.

(Even more bits could be used for encoding. This allows for using more of the image's total space but runs the risk of making the changes more visible. The last 2 bits is plenty for this notebook and most encodings. )

For example this image of the Death Star has all 3 of the original Star Wars Scripts encoded in it:

![alt text](https://github.com/PatrickBD/Image-Steganography-in-Python/blob/master/Death_Star_With_Scripts.jpg)

More impressively, this Death Star image has several layers of other images encoded in it like an Image Steganography nesting doll ending with the script for A New Hope (Death Star => X-Wing => R2D2 => Death Star Plans => New Hope Script)

![alt text](https://github.com/PatrickBD/Image-Steganography-in-Python/blob/master/Encoded_Death_Star_HD.jpg)




See the original notebook posting on Kaggle: https://www.kaggle.com/valkling/steganography-hiding-star-wars-scripts-in-images
