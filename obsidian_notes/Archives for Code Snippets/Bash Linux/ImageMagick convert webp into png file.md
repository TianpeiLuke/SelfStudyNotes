---
tags:
  - code
  - code_snippet
  - linux/webp
keywords: 
topics: 
language: bash
date of note: 2024-04-04
---

## Code Snippet Summary

>[!important]
>**Convert** an image from one format into another format


## Code

Use `mogrify` command from the  [**ImageMagick**](https://imagemagick.org/script/mogrify.php) tool to convert image. 

```bash
mogrify -format png *.webp
```

- `mogrify -format`: [reference](https://imagemagick.org/script/command-line-options.php#format)
	- When used with the mogrify utility, this option converts any image to the image [format](https://imagemagick.org/script/formats.php) you specify. For a list of image format types supported by ImageMagick, use [-list format](https://imagemagick.org/script/command-line-options.php#list).
	- 

- The **ImageMagick** command-line [tools](https://imagemagick.org/script/command-line-tools.php) can be as simple as this:

```bash
magick image.jpg image.png
```

-----------
##  Recommended Notes

- **Convert Between Image Formats**: Use the `magick` program to convert between image formats as well as resize an image, blur, crop, despeckle, dither, draw on, flip, join, re-sample, and much more.[reference](https://imagemagick.org/script/convert.php)
- **Inline Image Modification**: Use the `magick` `mogrify` program to resize an image, blur, crop, despeckle, dither, draw on, flip, join, re-sample, and much more. [main page](https://imagemagick.org/script/mogrify.php)
	- `mogrify -format`: [command line interface](https://imagemagick.org/script/command-line-processing.php)

- [How to Convert PNG to JPG on Ubuntu via Command](https://ubuntuhandbook.org/index.php/2013/07/how-to-convert-png-to-jpg-on-ubuntu-via-command/)