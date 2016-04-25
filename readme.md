# Web Optimization Project
The source code of the website to optimize is [here](https://github.com/udacity/frontend-nanodegree-mobile-portfolio).

## Introduction
In this repository you can find:
*   the source directory, `src/`, including the source code of the website to optimize
*   the distribution directory, `dist/`, including the final code of website optimized
*   the tools directory, `tools/`, including the files to run the code
*   this file, **readme.md**, documentation file

Developer tools I used to code the project:
*   my OS is **Ubuntu 14.04 LTS (Trusty Tahr)**
*   my code editor is **Sublime Text**
*   my browsers are **Chromium** and **Google Chrome Dev**
*   my readme editor is **haroopad**

Tools used to run and to manage the files (*tools directory*):
* **ngrok-stable-linux-amd64.zip**: tool that creates a secure tunnel on the local machine along with a public URL you can use for browsing your local site.
* **GzipSimpleHTTPServer.py**: web server based on SimpleHTTPServer with the manage of compression and caching. Taken from [here](https://github.com/ksmith97/GzipSimpleHTTPServer) with some minor modifications made by me.
* **Gruntfile.js**, **package.json**: grunt files used to minify css, js, html, compress images and other useful stuff.

Testing Tools:
* For the **Website Performance Optimization** part I used to test the performance:
  * The **PageSpeed** tool included in Chrome DevTools
  * `http://developers.google.com/speed/pagespeed/`
  * `http://gtmetrix.com/`
* For the **Browser Rendering Optimization** part I used to test the performance:
  * The **Chrome/Chromium DevTools**. My DevTools is rather different from the one I saw in Udacity video. I have less options and views or at least I couldn't achieve to get the same informations (even setting the experimental stuff).

## Download

`$ git clone https://github.com/svankj/Website-Optimization-Final-Project.git`

## Usage

Just launch the web server GzipSimpleHTTPServer (`python -m GzipSimpleHTTPServer 8000`) from terminal opened in the `dist/` directory. Then from the same directory run from terminal the tool ngrok (`.ngrok http 8000`). Then copy the public URL you get from ngrok in the browser (e.g. Chrome).

## Documentation
Some notes on the project:
  * I made only optimization modifications, then it is still the website of Cameron Pittman.
  * All my comments in the files css, html, js have the prefix `TODO:`.
  * Added the Udacity favicon missing.
  * There are compress files (html, css, js) and the files for documentation that end with `-dev` suffix.

The optimization is divided in two part:

1.  Website Performance Optimization:
    *   Inline little files css and js
    *   Compressed images using `grunt imagemin`
    *   Added responsive images `<picture>` using `grunt responsive_images`
    *   Minify css, html, js files using `grunt cssmin`, `grunt htmlmin`, `grunt minified`
    *   Set compression and caching by web server **GzipSimpleHTTPServer**
2.  Browser Rendering Optimization:
    *   Added in `.mover` element in the file **pizza.html**:
    ```css
        .mover {
            will-change: transform;
            -webkit-backface-visibility: hidden;
            backface-visibility: hidden;
        }
    ```
    *   Main modification in the file `main.js`:
        *   Changed the for loop reducing the operations and splitting the calculation part from the style modifications.
        *   Added `.requestAnimationFrame` for the scrolling part:
	```javascript
            window.addEventListener('scroll', function(e) {
                last_position = window.scrollY;
                if (!animate) {
                    window.requestAnimationFrame(function() {
                        updatePositions(last_position);
                        animate = false;
                    });
                }
            animate = true;
            });
	```

## License

>MIT License

>Copyright (c) 2016 svankj

>Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

>The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

>THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## About me
![svankj](https://avatars3.githubusercontent.com/u/17667643?v=3&s=100) | `svanky is a Freelance Developer`
--- | ---
