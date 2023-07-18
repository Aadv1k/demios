# Computer Vision in C

Experimental computer vision library in C

> I am trying to distill my knowledge into the [Robot's guide to seeing the world](https://aadv1k.gitbook.io/cv-guide), as an introductory guide to Computer Vision based on what I would have liked to had before I started learning this. I welcome any critique or suggestions, thanks!

- Smoothing
  - Gaussian blur: higher kernel will lead to more blurring, at the cost of speed
  - Median filter: higher sigma will give a smoother image 
  - Bilateral Filter: similar to Median but more performant
  - Box Filter: higher kernel size will give a more blurred image 
- Edge detection
  - Unsharp mask: emphasises the edges, higher sigma will make edges more pronounced at the cost of pixel tearing
  - Laplacian Filter (Difference of Gaussian): higher the kernel size thicker the edges. 
    Higher the sigma, less noisier the image.
  - Sobel operator: creates an image which emphasizes the edge, somewhat similar to Laplacian Filter
    but computationally better
- Color
  - Greyscale: convert image from RGB to 0..255 scale
- Thresholding
  - Global: "dumb" thresholding, given a sigma it will set all below it to white otherwise black 
  - Otsu's Method: compute a threshold dynamically based on the image histogram and then convert


> **Note**
> Almost all the functions of this library are arbitary and based on whatever came up on searching "image filtering algoritms"

## Build (Make)

```
git clone git@github.com:aadv1k/cv.c
cd cv.c/
make
```

## Build (without make)

> If you don't have make on windows, you can instead use the `build.bat`, it gets the job done. Even
> I couldn't figure out a non-dodgy way to install make on windows :/

```console
git clone git@github.com:aadv1k/cv.c
cd cv.c/
.\build.bat
```

## Build (unix)

```console
./build.sh
```

## Examples

> **Note**
> The filters are un-optimized, they work best on smaller images

```console
.\cv gray ..\data\img1.jpg .\output.png
.\cv sharpen --sigma 3 ..\data\img1.jpg .\output.png
.\cv blur --kernel 9 --sigma 5 ..\data\img1.jpg .\output.png
```

## Usage

```console
$ ./cv.exe
Usage:
        cv.exe <args> input output
Examples:
        cv.exe --blur --sigma 3.4 --kernel 5 input.png output.png
        cv.exe --gray input.png output.png
        cv.exe --median --kernel 3 input.png output.png
        cv.exe --sharpen --sigma 0.6 --kernel 3 input.png output.png
Options:
        --help                print this help message
        --blur, --gaussian    apply gaussian blur to the image
        --median              apply median filter to the image
        --sobel               apply sobel filter to the image
        --bilateral           apply bilateral filter to the image
        --box, --mean         apply box filter onto the image
        --laplacian           apply laplacian filter onto the image
        --gray                convert image to grayscale
        --sharpen             sharpen image via an unsharp mask
        --global-threshold    apply the global threshold filter over the image, `sigma` would be the threshold
        --otsu-threshold      apply the Otsu's threshold filter over the image
        --sigma               specify the sigma for the convolutions
        --kernel              define the kernel size for convolutions (if applicable)
```

## Gallery

> **Note**
> this showcases only some of the many avaliable filters

### Gaussian blur

```bash
.\bin\cv blur --kernel 9 --sigma 3 .\data\img1.jpg .\img1-gaussian-3-9.png
```

<div>
  <img src="./docs/.gitbook/assets/img1.jpg" width="50%" align="left">
  <img src="./docs/.gitbook/assets/gaussian-3-9.jpg" width="50%">
</div>

### Median filter

```bash
.\bin\cv median --kernel 9 .\data\img1.jpg ..\output.jpg
```

<div>
  <img src="./docs/.gitbook/assets/img1.jpg" width="50%" align="left">
  <img src="./docs/.gitbook/assets/median-9.jpg" width="50%">
</div>

### Unsharp mask

```bash
.\bin\cv sharpen --kernel 9 --sigma 1.2 .\data\img1.jpg ..\output.jpg
```

<div>
  <img src="./docs/.gitbook/assets/img1.jpg" width="50%" align="left">
  <img src="./docs/.gitbook/assets/sharpen-1-9.jpg" width="50%">
</div>

### Laplacian filter

```shell
.\bin\cv laplacian --kernel 3 --sigma 1.5 .\data\img1.jpg .\output.jpg
```

<div>
  <img src="./docs/.gitbook/assets/img1.jpg" width="50%" align="left">
  <img src="./docs/.gitbook/assets/laplacian-1-3.jpg" width="50%">
</div>


## Credits

gex.png: https://www.ign.com/games/gex-enter-the-gecko-gbc/articles
