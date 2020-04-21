# Week 8: Image performance

### How we can efficiently serve image assets?

![](https://media.giphy.com/media/QjIz1AqkGTszK/giphy.gif)

---

<iframe width="918" height="516" src="https://www.youtube.com/embed/2W-zJkIjF1k" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

- Usually, the page is downloaded with all its resources and files (images are often the most substantial part of this download)
- With lazy load a transparent placeholder is used until the image is needed (scrolled to)
- Ultimately makes the page faster



---

- Lazy-loading 
```javascript=
<img src="image.png" loading="lazy" alt="…" width="500" height="500">
```
- defers loading of the image until it is a *calculated distance* from the viewport (this can often be quite a high threshold)
  - the effective connection type
  - type of resource being loaded

- specify dimensions to prevent 'reflowing'

---

## How can we optimise image file size?

---

- Eliminate unnecessary image resources
- Leverage CSS3 effects where possible (gradients, shadows, etc.) 
- Use web fonts instead of encoding text in images

---

Vector vs Raster images
![](https://i.imgur.com/gSMEdui.png) ![](https://i.imgur.com/Kr4Lt3C.png)
Left: zoomed-in `raster` image 
Right: zoomed-in `vector` image

---

#### Optimizing vector images
- It is always a good idea to minify your SVG files by running through a tool like `svgo`.
- You can also apply `GZIP` compression to reduce its transfer size

---

#### Optimizing raster images
- deliver and optimize multiple variants of each image with the help of srcset and picture
- compression tools

---

#### Aside: raster image compression stratagies
- e.g. RGBA -> RGB (reduce colour palette available) (hence no of pixels/bytes/bit depth)
- nearby pixels with similar colours (delta encoding -- store differences of colours rather than each pixel)
- sensitivity of human eye 

---

#### Rastor Image formats

(new formats) JPEG-XR and WebP.
JPEG
PNG 
(GIF)

---

#### Lossy vs lossless compression
(all use lossy and lossless compression)
- lossy -- eliminates pixel data
- lossless -- compresses pixel data

- What is the "optimal"? 
-- Depends on the image contents 
-- Tradeoff between filesize and intricate detail 
-- No one universal setting. (use your judgement)


---

### Which format to use?

![](https://i.imgur.com/o9W1EcF.png)


---

![](https://i.imgur.com/E0Wxw3c.png)


---

## Responsive Images :100: 

![](https://media.giphy.com/media/idTKjnzYuyPYs/giphy.gif)

---

### How to make Responsive Images

- You can make your website run faster by setting the image size in px corretly, giving the right width and height for its use
- You might end up with different versions of the same image

i.e. desktop.jpg version and mobile.jpg version

- All you are doing is switching between different versions of the same image

---

### Use *srcset*, If you’re just changing resolutions

```htmlmixed=
<img src="small.jpg" 
srcset="medium.jpg 1000w, large.jpg 2000w" 
alt="this is a cute photo of the rugrats">
```
#### Give the brower the work of figuring out which image to use

![](https://media.giphy.com/media/Qh2MZDIHvZavK/giphy.gif =300x)

---

### So, How to use srcset? 

![](https://media.giphy.com/media/10yIEN8cMn4i9W/giphy.gif =500x)

---

```htmlmixed=
<img src="small.jpg" 
srcset="medium.jpg 1000w, large.jpg 2000w" 
alt="this is a cute photo of the rugrats">
```

- This *src="small.jpg"* can be considered the **fallback** so something will always show
- *medium.jpg 1000w* tells the browers that the image is 1280 pixels wide
- The brower would know **after** downloading it that the width is 1280px but by telling it now, it can make a decision right off the bat

---

```htmlmixed=
<img src="small.jpg" 
srcset="medium.jpg 1000w, large.jpg 2000w" 
sizes="(min-width: 800px) 50vw, 100vw"
alt="this is a cute photo of the rugrats">
```

“If the browser window is **wider** than **800px**, this image is probably going to be displayed about **half** the size of that. If it’s smaller, it’ll probably be full-width.”

You can leave size out, default is *sizes="100vw"*
*sizes="100vw"* is entire width of the viewport, 50vw is half, 33.3vw is a third
Think of *(min-width: 800px)  50vw* as a media query

---

## Questions 

![](https://media.giphy.com/media/TgF6xfH8V0mZcUyneP/giphy.gif)

---

## Useful resources

[Node.js tool for optimizing SVG files](https://github.com/svg/svgo)
[How to enable gzip compression](https://varvy.com/pagespeed/enable-compression.html)
[Responsive Images: If you’re just changing resolutions, use srcset.](https://css-tricks.com/responsive-images-youre-just-changing-resolutions-use-srcset/)
[Figuring Out Responsive Images](https://css-tricks.com/video-screencasts/133-figuring-responsive-images/)
