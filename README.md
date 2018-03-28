# Image to SceneGraph XML Conversion
This is a command line utility to convert image files to the SceneGraph XML files used in COMP-175 at Tufts University. A project in the class requies students to write an XML file creating an interesting scene; this utility generates such files. It can generate XML from most common image formats, including jpg, png, and gif, and supports various arguments for orienting the resulting scenes and for extruding pixels based on brightness values to give an illusion of depth. The output XML is printed to standard output.

# Command Line Arguments

| Option / Flag | Alternative (Long-Form) | Short description                                           | Type        | Requirements          | Detailed Description
|---------------|-------------------------|-------------------------------------------------------------|-------------|-----------------------|---------------------------
| N/A            | N/A               | path to image file to convert           | string      | must be a valid path  | Required option, specifies the path to an image file which is to be converted to an XML file.
| `-w`            | `--width`                  | desired width in pixels that image is to be resized to                | int      | must be >= 1 | Specifies the desired width in pixels that the image is to be resized to; recommended size is under 200px, as each pixel becomes a polygon in the 3D render. If the aspect ratio is such that this width would create a height that is less than 1, the program terminates with an error. If none is specified, 100px is used. Run with `-r` to use the original file size.
| `-s`            | `--shape`                 | shape (primitive) to use for each pixel                                | string     | N/A    | Specifies which primitive to use to draw the pixels of the image; typical values of 'square', 'cylinder', 'sphere', or 'cone' are expected, though anything supported by the XML parser which produces the 3D render will work.
| `-r`            | `--no-resize`                  | turns off resizing of the input image    | N/A         | N/A                   | Disables the resizing of the image; if `-w` is specified, the image is still not resized.
| `-n`            | `--noise`                  | turns on noise in the pixel directions    | N/A         | N/A                   | Points pixels in directions slightly off from straight along the Z-axis with a gaussian distribution, giving a blurred effect.
| `-e`            | `--extrude`                  | turns on extrusion of pixels    | N/A         | N/A                   | Rather than drawing each pixel as a unit primitive of the type specified by `-s`, this makes them scaled forward in the Z-direction by an amount proportionate to the brightness value of the pixel.
| `-i`            | `--invert`                  | invert the extrusion     | N/A         | N/A                   | By default the extrusion is such that lighter pixels come forward more; this reverses that so darker pixels are in the foreground.
| `-c`            | `--extrude-const`                  | the amount of extrusion to use     | float         | must be > 0       | The constant to multiply the extrusion by; default is 1, for values between 0 and the width and height of the pixels, but any value can be chosen for a more extreme effect.
| `-ax`            | `--anglex`                  | the angle to rotate the image by about the X-axis     | float         | N/A       | The angle about the X-axis to rotate the entire image object in 3D space; value is expected to be in degrees.
| `-ay`            | `--angley`                  | the angle to rotate the image by about the Y-axis     | float         | N/A       | The angle about the Y-axis to rotate the entire image object in 3D space; value is expected to be in degrees.
| -h            | --help                  | help page                                                   | N/A         | N/A                   | Displays a summary of this information.

# Examples
![Gradient](https://github.com/forsooth/im2xml/raw/master/examples/grad.png)
![Dragon](https://github.com/forsooth/im2xml/raw/master/examples/dragon.png)
![Sidescroller Game](https://github.com/forsooth/im2xml/raw/master/examples/sidescroll.png)
![Sidescroller Game](https://github.com/forsooth/im2xml/raw/master/examples/blacksmith.png)
![Sidescroller Game](https://github.com/forsooth/im2xml/raw/master/examples/city.png)
![Sidescroller Game](https://github.com/forsooth/im2xml/raw/master/examples/sun.png)
