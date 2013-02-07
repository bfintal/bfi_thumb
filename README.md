bfi_thumb
=========

On the fly image resizer / cropper / grayscaler / colorizer / opacitor :) for WordPress

Bfi_thumb resizes image on the fly using WordPress' Image Editor classes, thus supports both Imagick and GD and switches automatically depending on what's available. The default Image Editors only have a handful of basic functions (crop, resize, rotate, etc), bfi_thumb also extends these classes to include these new functions:
* Grayscale
* Color (colorize)
* Opacity
* Negate

Bfi_thumb stores previously created images in WP's default uploads directory, and uses those for future calls. The script automatically checks for updates on the original image then re-creates new images when needed. Any image can be used as long it is in your WordPress instance.

The code was inspired by the awesome [Aqua Resizer](https://github.com/sy4mil/Aqua-Resizer/blob/master/aq_resizer.php)

<hr>

Why Make a New One?
===================

Aqua Resizer is awesome, WP's Image Editor is awesome, Timthumb is awesome.

When WP reached 3.5 and introduced the Image Editor class, as a theme author I couldn't anymore use Timthumb in my WP themes. An alternative was to use Aqua Resizer instead. Although it did the job quite well, I needed some of the functionalities supported by Timthumb.. I needed to be allowed to grayscale, color tint images and change the opacity of images all while resizing them. I couldn't find anything that did everything I wanted, so I made BFI_Thumb.

<hr>

Usage
=====

1. Include / require BFI_Thumb.php into your WordPress files.

```php
require_once('BFI_Thumb.php');
```

2. Call the function to get the image URL

```php
$params = { 'width' => 400 };
echo "<img src='" . bfi_thumb( "URL-to-image.jpg", $params ) . "'/>";
```
    
**$params is an associative array containing the actions to perform on your image.**

Examples:

```php
// Resize by width only
$params = {'width' => 400};
bfi_thumb("URL-to-image.jpg", $params);

// Resize by width and height
$params = {'width' => 400, 'height' => 300};
bfi_thumb("URL-to-image.jpg", $params);

// You can't resize by height alone

// Crop
$params = {'width' => 400, 'height' => 300, 'crop' => true};
bfi_thumb("URL-to-image.jpg", $params);

// Change opacity (makes your image into a PNG)
$params = {'opacity' => 80}; // 80% opaque
bfi_thumb("URL-to-image.jpg", $params);

// Grayscale
$params = {'grayscale' => true};
bfi_thumb("URL-to-image.jpg", $params);

// Colorize
$params = {'color' => '#ff0000'};
bfi_thumb("URL-to-image.jpg", $params);

// Negate
$params = {'negate' => true};
bfi_thumb("URL-to-image.jpg", $params);

// Multiple parameters
$params = {'width' => 400, 'height' => 300, 'opacity' => 50, 'grayscale' => true, 'colorize' => '#ff0000'};
bfi_thumb("URL-to-image.jpg", $params);
```

<hr>

License
=======
GPL 3.0

It's not required but I appreciate if you attribute and/or link back if you find this helpful :)

<hr>

Social Stuff
============

Twitter: (@bfintal)[https://twitter.com/bfintal] & (@gambitph)[https://twitter.com/gambitph]
