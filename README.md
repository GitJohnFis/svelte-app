# svelte-app
<hr>

**Udemy crash course**

1. Install dependencies and templates
2. Create svelte-app
3. Create tests for app
4. Run app on local machine
5. more...

# 🚧 Under Construction 🚧

<img src="https://media.giphy.com/media/3o7TKtnuHOHHUjR38Y/giphy.gif" width="128" style="text-align: center;" />

This project is currently a work in progress. Stay tuned for updates!


You can add some HTML (actually XHTML) and CSS inside a <foreignObject> tag inside of an svg file and then embed that inside of an <img> tag in your GitHub README.

This is a simple animation in CSS that changes the color of the h1 text:

h1 {
  color: red;
  animation: myanimation 2s infinite;
}

@keyframes myanimation {
  from {
    color: red;
  }
  to {
    color: yellow;
  }
}
<h1>Hello world!</h1>
Full page
You can embed the style and HTML into a <foreignObject> tag inside of an svg like so:

example.svg

<svg fill="none" viewBox="0 0 400 400" width="400" height="400" xmlns="http://www.w3.org/2000/svg">
    <foreignObject width="100%" height="100%">
        <div xmlns="http://www.w3.org/1999/xhtml">
            <style>
            h1 {
                color: red;
                animation: mymove 2s infinite;
            }

            @keyframes mymove {
                from {
                    color: red;
                }
                to {
                    color: yellow;
                }
            }
            </style>
            <h1>HELLO WORLD!</h1>
        </div>
    </foreignObject>
</svg>
