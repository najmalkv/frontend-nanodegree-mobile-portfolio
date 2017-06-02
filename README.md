## Frontend Nanodegree Web Optimization Project - Mobile Portfolio

This is my solution to web optimisation project of the frontend nanodegree from Udacity. It consists of the optimizations I have made to the provided source code to meet specifications of the project rubric. Below mentioned is a gist of the steps I took to optimize the project.

##### Optimizing the Critical rendering path and acheiving a pagespeed score of greater than 90

* Compressed and minified all the assets(html, css, js & images) using the gulp build system.
* Removed render blocking css file requests and inlined it to shorten the critical rendering path.
* Removed the link to web fonts as it wasn't adding much value and it was affecting the critical rendering path.
* Also made all the requests for analytics scripts `async` to remove its influence on the critical rendering path.
* Reduced the dimensions of pizzeria.jpg to the largest possible view dimensions since it was too big for any screen.

##### Optimizations made to views/js/main.js to make views/pizza.html render with a consistent frame-rate at 60fps when scrolling.

* Moved the `document.body.scrollTop` , in the `updatePositions` function, outside the for loop to avoid layout thrashing.
* Used `requestAnimationFrame` instead of the scroll listener on `updatePositions` function.
* Stored the moving pizza elements into an array as they were created and used it in the `updatePositions` function rather than querying the dom for it.

##### Reduced the time to update the pizza size using the pizza slider on views/pizza.html to under 5ms.

* Removed the `determineDX` function by making the algorithm to detemine the size simpler. This got rid of layout thrashing that was occuring.
* Saved the random pizza container elements to a variable and reused it instead of querying the dom repeatedly.
## Getting Started

### Installation
To get the project running on your local machine firstly take a clone of this repo onto your local machine. Then `cd` into the root directory on your CLI tool(eg. CMD prompt or Terminal) and then run `npm install`. This will install all the node packages you require to run the project.

```
npm install
```

### How to Run

The project is equipped with a gulp build system. You can follow the below mentioned methods to run the website depending on the build you prefer.

 _Note:_ `cd` into the root folder on your CLI tool and then run the commands.

To run the devolopment build with auto reload use the following command:
```
gulp serve
```

To run the production build use the following command:
```
gulp serve:dist
```

### How to Build for production

To get the production build use the following command from the root folder:
```
gulp
```

This command will optimize the files and output it to the **dist** folder. Use the contents of this folder for your production hosting.

## LICENSE

MIT License

Copyright (c) 2017 Najmal K V

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.