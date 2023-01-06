---
subject : DIP
category: 
- lecture-notes
module  : 
---
#Unlinked 
#incomplete 
2023-01-03

>Links: [[DIP MOC]]

**image**: defined as a 2D function g(x,y) where x and y are spatial or plane coordinates

**intensity**: for a image represented by g(x,y), the value g at coordinates x and y is the intensity or the gray level

**digital image**: when x, y and the amplitude levels of g are all finite and discrete in quantities, the image is said to be a digital image.

**pixls**: digital image is composed of finite no. of elements, each of which has a particular location and value, these are called pixels, image elements, etc.

>[!NOTE]
>the coordinate system is the fourth quadrant (from usual), but y is not negative

every image is made with a matrix of color values for x,y location.

in modern imaging, we have the range of intensity represented as bits with values ranging from 0 to 255 
0 -> black
1 -> white

for a 420x420 image, if each pixel is of 8 bits, we need storage of 420x420x8 bits.

bitmap -> matrix of intensity values for x,y locations where the range is given by one bit

for more than one bit, it is called graymap

perspective projection - lines going spheircally
orthogonal projection - when lines going 90 degrees

in a digital image, the x and y locations are discrete (unlike the real world, where it is continuous)

## fundamental steps in DIP
- image acquisition
- img enhancement
- image restoration
- morphlogical processing
- segmentation (CV)
- representation and description (CV)
- object recognition (CV)
- image compression
- colour image processing

