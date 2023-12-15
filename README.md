# Simple Image Generation - Hugo Plugin for Micro.blog 🎞️
Yet _another_ image plugin for Micro.blog, allowing customization of image tag generation with Shortcodes, without having to write HTML. The plugin uses various parameter (see below) to generate HTML within a `<figure>` element.

![Screen shot of HTML and the resulting image](https://raw.githubusercontent.com/lostinhaste/simple-image-plugin/main/icon.png)

-----

## Parameter List / Key

Below are a list of the various parameters the Plugin can use when generating HTML.

| Parameter | Required | Description |
|---|---|---|
| `src` | Yes | Link to the image. |
| `alt` | No | Used to generate alternative text for screen readers, it's use is _highly_ recommended for accessability purposes.  |
| `caption` | No |  |
| `title` | No | If provided, generates an `h4` tag within the `<figure>` element. |
| `attr` | No * | If provided, used at the text of the `<a />` within the `<figure>` element; requires the `attrlink` parameter. |
| `attrlink` | No * | If provided, is used within the _href_ element of the `<a>` tag ; requires the `attr` parameter. |
| `link` | No | If provided, wraps the `<img />` tag in an anchor tag (`<a />`). |

_* The `attr` and `attrlink` depend on each other, using ones means the other should be used._

## Examples

Below are a few examples of how to use the plugin.

### Image Only

The only required parameter for the shortcode / plugin is _src_.

```hugo
{{< simple-image src="https://micro.lostinhaste.com/uploads/2023/winter-ice-and-light.jpg" >}}
```

**Result:**

```html
<figure>
    <img src="https://micro.lostinhaste.com/uploads/2023/winter-ice-and-light.jpg">
</figure>
```

### Clickable Image

Including the _link_ parameter will allow the image to be clickable.

```hugo
{{< simple-image src="https://micro.lostinhaste.com/uploads/2023/winter-ice-and-light.jpg" link="https://micro.lostinhaste.com/2023/09/29/september-microblog-photo.html" >}}
```

**Result:**

```html
<figure>
    <a href="https://micro.lostinhaste.com/2023/09/29/september-microblog-photo.html">
        <img src="https://micro.lostinhaste.com/uploads/2023/winter-ice-and-light.jpg">
    </a>
</figure>
```

### Image with Caption / Alt

Adding text in the  _alt_ parameter will result in the generation of an image with alternative text. If the _caption_ parameter is used, additional text will be rendered near the image, within the `figure` html tag.

```hugo
{{< simple-image src="https://micro.lostinhaste.com/uploads/2023/winter-ice-and-light.jpg" alt="View of the St. Lawrence River, with ice chunks occupying most of the surface, at night, with houses covered in snow and streets with lights at the bottom of the picture. On the upper part of the picture, across the river, lights can be seen up and down a bluff, with a few well-light buildings prominent in the cloudy night sky." caption="An icy view of lower Old Town Quebec during winter." >}}
```

**Result:**

```html
<figure>
    <img src="https://micro.lostinhaste.com/uploads/2023/winter-ice-and-light.jpg" alt="View of the St. Lawrence River, with ice chunks occupying most of the surface, at night, with houses covered in snow and streets with lights at the bottom of the picture. On the upper part of the picture, across the river, lights can be seen up and down a bluff, with a few well-light buildings prominent in the cloudy night sky.">
    <figcaption>
        <p>
            An icy view of lower Old Town Quebec during winter.
        </p> 
    </figcaption>
</figure>
```

### Image with Title / Caption

Adding the _title_ parameter will generate an `h4` html tag within the greater `figure` html tag.

```hugo
{{< simple-image src="https://micro.lostinhaste.com/uploads/2023/winter-ice-and-light.jpg" title="Winter in Quebec" caption="An icy view of lower Old Town Quebec during winter." >}}
```

**Result:**

```html
<figure>
    <img src="https://micro.lostinhaste.com/uploads/2023/winter-ice-and-light.jpg" alt="An icy view of lower Old Town Quebec during winter.">
    <figcaption>
        <h4>Winter in Quebec</h4>
        <p>
            An icy view of lower Old Town Quebec during winter.
        </p> 
    </figcaption>
</figure>
```

### Image with Link

Including the _attr_ and _attrlink_ parameters will allow for the creation of a hyperlink within the `figure` html tag element.


```hugo
{{< simple-image src="https://micro.lostinhaste.com/uploads/2023/winter-ice-and-light.jpg" attr="Original Post" attrlink="https://micro.lostinhaste.com/2023/09/29/september-microblog-photo.html" >}}
```

**Results:**

```html
<figure>
    <img src="https://micro.lostinhaste.com/uploads/2023/winter-ice-and-light.jpg">
    <figcaption>
        <p>
            <a href="https://micro.lostinhaste.com/2023/09/29/september-microblog-photo.html"> 
                Original Post
            </a> 
        </p> 
    </figcaption>
</figure>
```

## Change Logs

| Version | Date | Description |
|---|---|---|
| 1.0.1 | December 15, 2023 | Updating the README.md file with a hard-coded link to the project image (allows said image to appear in Micro.blog). |
| 1.0.0 | November 3, 2023 | The initial release of the project. |