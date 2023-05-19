# spatial domain
## 1. Intensity Transform functions
### image negatives
$$s = T(r) = L-1-r$$
### log transformation
- maps a narrow range of low intensity to values to wider range of output levels
- inverse log transform does the opposite
$$s = c \cdot log(1+r)$$
### Power Law (Gamma) transformation
- used for brightening and darkening just like log transform, but has much more range (thanks to $\gamma$)
- **gamma correction**: process to correct output from imaging devices
	- CRT have intensity-to-voltage response - a power function with $\gamma$ about 1.8 to 2.5. this makes the image much darker. 
	- we use gamma correction using $\gamma = \frac{1}{2.5} = 0.4$ to obtain the original image
$$s = c \cdot r^{\gamma}$$
### piecewise linear transformation
- implementing the above transforms in a more complex way
- there are different methods:

#### contrast stretching
- process of expanding the range of intensity levels so that it spans the full intensity range of the device.
- this is done using a *piecewise function* with controlling points $(r_1,s_1)$ and $(r_2,s_2)$.
- if $r_1=s_1$ and $r_2=s_2$,we get a *thresholding function*
	- creates a binary image
	- any input intensity value below $r_1$ has output as $s_1$
	- same for $r_2$ to $s_2$
- the function is monotonically increasing

#### intensity level / grey level slicing
- *highlighting a specific range* of intensities (of interest)
- two approaches
	- without background
	- with background

#### bit plane slicing
- each pixel's intensity value is stored in bits format
- suppose the image is composed of 8 bits
- separating each place of bit for respective $(x,y)$ is bit plane slicing
- higher order bit-planes hold the significant data about the image
- lower order bit-planes hold other subtle info

## 2. histogram processing
### equalization
### specification / matching

## 3. spatial filtering
### spatial correlation and convolution

## 4. smoothening spatial filters
### linear filters
### order-statistic filters

## 5. sharpening spatial filters
### laplacian
### derivative
### unmask and high-boost
### gradient

---
# frequency domain
## Fourier series
## Impulses and sampling
## Fourier transform
## convolution
## smoothening filters
## sharpening filters

---
# segmentation


---
# color image
## color models
## pseudocolor
## color transforms

---
# compression
## fundamentals
## huffman coding
## LZW coding
## arithmetic coding
## golomb coding
## shannon-fano coding
## run-length coding
## bit plane
## predictive coding

---
# morphology


---
# industrial image processing
