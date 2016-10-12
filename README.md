# LiquidColor

## Liquid color tooling
LiquidColor is a small snippet based library for color type conversions and basic manipulations in for Shopify written with Liquid. Since Shopify's new section and block color settings can not be processed through SCSS this is a reliable way to convert hex values to RGB, HSL and detect if a color is light or dark.

## Usage
In a Shopify template, section or block add `{% include 'liquidcolor' with my_color %}` to generate a range of useful liquid variables based on the inputted hex color.

```liquid
{% assign my_color = '#3467ad' %}
{% include 'liquidcolor' with my_color %}

<ul>
  <li>Hex: {{ liquidcolor_hex }}</li>
  <li>RGB: rgb({{ liquidcolor_rgb }})</li>
  <li>HSL: hsl({{ liquidcolor_hsl }})</li>
  <li>Color is more than 50% light: {{ liquidcolor_isLight }}</li>
  <li>Text on the color should be: {{ liquidcolor_getContrastColor }}</li>
</ul>
```

### RGB, RGBA
```liquid
RGB: rgb({{ liquidcolor_rgb }})
RGBA: rgb({{ liquidcolor_rgb }}, 1)
Red channel: {{ liquidcolor_rgb_r }}
Green channel: {{ liquidcolor_rgb_g }}
Blue channel: {{ liquidcolor_rgb_b }}
Dominate channel: {{ liquidcolor_rgb_max_channel }}
```

### HSL, HSLA
```liquid
HSL: hsl({{ liquidcolor_hsl }})
HSLA: hsla({{ liquidcolor_hsl }}, 1)
Hue: {{ liquidcolor_hsl_h }}°
Saturation: {{ liquidcolor_hsl_s }}%
Lightness: {{ liquidcolor_hsl_l }}%
```

### Methods
```liquid
Color is more than 50% light
isLight: {{ liquidcolor_isLight }}

Contrast color (white or black) based on isLight value
getContrastColor: {{ liquidcolor_getContrastColor }}
```

## Credits
Hex to RGB conversion thanks to Grant Eagon
- https://github.com/granteagon/Shopify-hex2rgb.liquid

Help with the math on RGB to HSL conversions
- http://www.niwa.nu/2013/05/math-behind-colorspace-conversions-rgb-hsl/
- https://github.com/bgrins/TinyColor   
