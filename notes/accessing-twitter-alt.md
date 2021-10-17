# CSS code to display alt on Twitter, and other such tweaks

Works with the *Stylus* extension on Chrome, Firefox, Opera, +?. Codes #1, #3 and #4 come directly from Twitter user @lunasorcery and [this great thread of hers](https://twitter.com/lunasorcery/status/1361796263721775104 "this great thread of hers"); #2 is my frankenstein off of her code.

The snippets can be combined into one larger CSS code, or they can be added to Stylus as separate codes that can be individually toggled on and off. I personally always have the red frame code (#3) enabled, but sometimes disable the only alt code (#2).

## 1. Display only images with alt text
Images without alt text won\'t load and will be replaced by \"image\" in whichever language you have your Twitter set up. This can be circumvented by clicking on the space where the image would be, which will open it in the Twitter viewer and will display properly.
```css
div[aria-label="Image"]{
    background: #000;
    margin: 0 !important;
}
div[aria-label="Image"]:after{
    content:"Image";
    color:#fff;
    text-align:center;
    font-size:50pt;
    font-family:sans-serif;
    padding:20px;
}
div[aria-label="Image"] *{
    display:none;
}
```

## 2. Display no images whatsoever, only their alt
If an image has no alt, it will read \"image\" only, in whichever language you have your Twitter set up.
```css
div[data-testid="tweetPhoto"] {
    margin: 0 !important;
}
div[data-testid="tweetPhoto"]:after {
    content: attr(aria-label);
    color:#fff;
    font-family:sans-serif;
    padding:20px;
}
div[data-testid="tweetPhoto"] *{
    display:none;
}
```

## 3. Display a big red frame around images with no alt
```css
div[aria-label="Image"] {
    margin: 0 !important;
    border: 20px solid #f00;
}
```

## 4. Add a banner with the alt text on top of the images displayed
```css
div[data-testid="tweetPhoto"]:not([aria-label="Image"]) {
    margin: 0 !important;
}
div[data-testid="tweetPhoto"]:not([aria-label="Image"]):after {
    content: attr(aria-label);
    background: rgba(0,0,0,.75);
    color: #fff;
    padding: 10px;
    font-family: sans-serif;
}
```

If you have any more code suggestions for Twitter accessibility, I\'d be happy to add them here (with proper credit, of course)!