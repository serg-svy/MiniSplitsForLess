# Image Optimization Guide for MiniSplitsForLess

Comprehensive guidelines for optimizing images for SEO and performance.

## Table of Contents

1. [Image File Requirements](#image-file-requirements)
2. [File Naming Conventions](#file-naming-conventions)
3. [Alt Text Guidelines](#alt-text-guidelines)
4. [Image Dimensions by Type](#image-dimensions-by-type)
5. [Compression & Format](#compression--format)
6. [Shopify-Specific Guidelines](#shopify-specific-guidelines)
7. [Structured Data for Images](#structured-data-for-images)
8. [Implementation Checklist](#implementation-checklist)

---

## Image File Requirements

### General Requirements

| Requirement | Specification |
|-------------|---------------|
| Format | WebP (preferred), JPEG, PNG |
| Max File Size | 500KB for product images, 200KB for thumbnails |
| Color Profile | sRGB |
| Resolution | 72 DPI (web standard) |
| Background | White or transparent for products |

### Quality Guidelines

- **Product Images:** High quality, sharp, well-lit
- **No Watermarks:** Remove any watermarks or logos over products
- **Consistent Style:** Maintain consistent photography style across catalog
- **Professional Appearance:** Studio-quality lighting preferred

---

## File Naming Conventions

### Format

```
[brand]-[product-type]-[btu]-[descriptor]-[view].webp
```

### Examples

**Good File Names:**
- `cooper-hunter-mini-split-12000-btu-indoor-unit-front.webp`
- `olmo-ductless-ac-9000-btu-outdoor-condenser-side.webp`
- `mini-split-installation-kit-25ft-copper-line.webp`
- `multi-zone-mini-split-4-zone-system-complete.webp`

**Bad File Names:**
- ❌ `IMG_0234.jpg`
- ❌ `product-photo-1.png`
- ❌ `CH12K_v2_FINAL.jpeg`
- ❌ `image (1).jpg`

### File Naming Rules

1. Use lowercase letters only
2. Use hyphens (-) to separate words
3. Include relevant keywords
4. Be descriptive but concise
5. Include product identifiers (BTU, model)
6. Indicate image view/angle

---

## Alt Text Guidelines

### Purpose of Alt Text

1. **Accessibility:** Screen readers for visually impaired users
2. **SEO:** Search engines use alt text to understand images
3. **Fallback:** Displays when images fail to load

### Alt Text Formula

```
[Brand] [Product Name] [Key Feature/Spec] - [Descriptor/View]
```

### Examples by Image Type

#### Product Main Images
```html
<!-- Good -->
<img src="..." alt="Cooper & Hunter 12000 BTU Ductless Mini Split AC Indoor Unit - White">
<img src="..." alt="OLMO 18000 BTU Multi-Zone Mini Split Outdoor Condenser Unit">

<!-- Bad -->
<img src="..." alt="product image">
<img src="..." alt="mini split">
<img src="..." alt="">
```

#### Product Detail/Feature Images
```html
<img src="..." alt="Cooper & Hunter Mini Split Remote Control with LCD Display">
<img src="..." alt="Mini Split Installation Kit - 25ft Copper Line Set and Cables">
<img src="..." alt="Ductless AC Indoor Unit Showing Air Vents and LED Display">
```

#### Lifestyle/Installation Images
```html
<img src="..." alt="Mini Split Installed in Modern Living Room Above Sofa">
<img src="..." alt="Outdoor Condenser Unit Mounted on Wall Bracket">
<img src="..." alt="HVAC Technician Installing Ductless Mini Split System">
```

#### Infographics/Diagrams
```html
<img src="..." alt="Mini Split BTU Size Chart - Room Square Footage to BTU Guide">
<img src="..." alt="Diagram Showing Single Zone vs Multi Zone Mini Split System">
<img src="..." alt="SEER Rating Comparison Chart for Energy Efficiency">
```

### Alt Text Best Practices

| Do | Don't |
|----|-------|
| Be descriptive and specific | Use generic terms like "image" or "photo" |
| Include relevant keywords naturally | Stuff keywords unnaturally |
| Keep under 125 characters | Write excessively long descriptions |
| Describe what's in the image | Describe what's not visible |
| Use proper capitalization | Use ALL CAPS |
| Be unique for each image | Copy the same alt text for multiple images |

---

## Image Dimensions by Type

### Product Images

| Image Type | Dimensions | Aspect Ratio | Use Case |
|------------|------------|--------------|----------|
| Main Product | 2048 x 2048 px | 1:1 | Primary product display |
| Product Thumbnail | 600 x 600 px | 1:1 | Collection pages, cart |
| Zoom Image | 2048 x 2048 px | 1:1 | Hover zoom functionality |
| Gallery Images | 1200 x 1200 px | 1:1 | Product page gallery |

### Collection & Banner Images

| Image Type | Dimensions | Aspect Ratio | Use Case |
|------------|------------|--------------|----------|
| Collection Banner | 1920 x 600 px | 3.2:1 | Collection page headers |
| Homepage Hero | 1920 x 800 px | 2.4:1 | Homepage slideshow |
| Category Card | 800 x 600 px | 4:3 | Category navigation |
| Blog Featured | 1200 x 628 px | 1.91:1 | Blog post thumbnails |

### Mobile Considerations

- Provide responsive image variants
- Use `srcset` for different screen sizes
- Test on multiple device sizes
- Consider data usage for mobile users

---

## Compression & Format

### Recommended Formats

| Format | Best For | Compression |
|--------|----------|-------------|
| WebP | All web images (preferred) | Lossy/Lossless |
| JPEG | Photographs, product images | Lossy |
| PNG | Graphics with transparency | Lossless |
| SVG | Logos, icons, simple graphics | Vector |

### Compression Guidelines

**Product Images:**
- WebP: Quality 80-85%
- JPEG: Quality 80-85%
- Target size: 100-300KB

**Thumbnails:**
- WebP: Quality 75-80%
- JPEG: Quality 75-80%
- Target size: 20-50KB

**Banners/Heroes:**
- WebP: Quality 80-85%
- JPEG: Quality 80-85%
- Target size: 200-400KB

### Compression Tools

**Free Online Tools:**
- [Squoosh](https://squoosh.app/) - Google's image optimizer
- [TinyPNG](https://tinypng.com/) - PNG/JPEG compression
- [ImageOptim](https://imageoptim.com/) - Mac app

**Shopify Apps:**
- Crush.pics
- Image Optimizer
- TinyIMG

**Command Line:**
```bash
# Convert to WebP with cwebp
cwebp -q 80 input.jpg -o output.webp

# Optimize JPEG with jpegoptim
jpegoptim --max=85 --strip-all image.jpg

# Optimize PNG with pngquant
pngquant --quality=65-80 image.png
```

---

## Shopify-Specific Guidelines

### Shopify Image Upload Best Practices

1. **Upload High Resolution:** Shopify generates multiple sizes automatically
2. **Use Square Images:** 1:1 ratio works best for product grids
3. **Consistent Backgrounds:** White backgrounds recommended
4. **File Size Limits:** Max 20MB per image, but keep under 500KB

### Shopify Liquid Image Handling

```liquid
{% comment %} Responsive product images with srcset {% endcomment %}
<img
  src="{{ product.featured_image | image_url: width: 800 }}"
  srcset="
    {{ product.featured_image | image_url: width: 400 }} 400w,
    {{ product.featured_image | image_url: width: 600 }} 600w,
    {{ product.featured_image | image_url: width: 800 }} 800w,
    {{ product.featured_image | image_url: width: 1000 }} 1000w,
    {{ product.featured_image | image_url: width: 1200 }} 1200w
  "
  sizes="(min-width: 1200px) 600px, (min-width: 768px) 50vw, 100vw"
  alt="{{ product.featured_image.alt | escape }}"
  loading="lazy"
  width="{{ product.featured_image.width }}"
  height="{{ product.featured_image.height }}"
>
```

### Lazy Loading Implementation

```liquid
{% comment %} Native lazy loading for below-fold images {% endcomment %}
{% for image in product.images offset: 1 %}
  <img
    src="{{ image | image_url: width: 800 }}"
    alt="{{ image.alt | escape }}"
    loading="lazy"
    decoding="async"
    width="{{ image.width }}"
    height="{{ image.height }}"
  >
{% endfor %}
```

### Image Alt Text in Shopify

```liquid
{% comment %} Best practice for alt text in Shopify {% endcomment %}

{% comment %} Use image alt if set, fallback to product title {% endcomment %}
alt="{{ image.alt | default: product.title | escape }}"

{% comment %} More descriptive fallback {% endcomment %}
alt="{% if image.alt != blank %}{{ image.alt }}{% else %}{{ product.title }} - {{ product.vendor }}{% endif %}"
```

---

## Structured Data for Images

### Product Image Schema

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Cooper & Hunter 12000 BTU Mini Split",
  "image": [
    "https://minisplitsforless.com/images/ch-12000-main.webp",
    "https://minisplitsforless.com/images/ch-12000-side.webp",
    "https://minisplitsforless.com/images/ch-12000-installed.webp",
    "https://minisplitsforless.com/images/ch-12000-remote.webp"
  ]
}
```

### ImageObject Schema

```json
{
  "@context": "https://schema.org",
  "@type": "ImageObject",
  "contentUrl": "https://minisplitsforless.com/images/ch-12000-main.webp",
  "name": "Cooper & Hunter 12000 BTU Mini Split Indoor Unit",
  "description": "Front view of the Cooper & Hunter 12000 BTU ductless mini split indoor wall-mounted unit in white",
  "width": "1200",
  "height": "1200",
  "encodingFormat": "image/webp"
}
```

### Open Graph Image Tags

```html
<!-- For social sharing -->
<meta property="og:image" content="{{ product.featured_image | image_url: width: 1200 }}">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="1200">
<meta property="og:image:alt" content="{{ product.featured_image.alt | default: product.title }}">

<!-- Twitter Card -->
<meta name="twitter:image" content="{{ product.featured_image | image_url: width: 1200 }}">
<meta name="twitter:image:alt" content="{{ product.featured_image.alt | default: product.title }}">
```

---

## Implementation Checklist

### Before Upload

- [ ] Image is high quality and properly lit
- [ ] Background is white or transparent (for products)
- [ ] Image is cropped appropriately
- [ ] File is named using conventions above
- [ ] Image is compressed to appropriate file size
- [ ] Format is WebP (preferred) or optimized JPEG/PNG

### During Upload

- [ ] Alt text is written and descriptive
- [ ] Correct dimensions for intended use
- [ ] Multiple angles uploaded for products
- [ ] Images ordered appropriately (main image first)

### After Upload

- [ ] Verify images display correctly on all devices
- [ ] Check page load speed hasn't degraded
- [ ] Validate structured data includes images
- [ ] Test social sharing image previews
- [ ] Confirm lazy loading works for below-fold images

### Periodic Audit

- [ ] Review images for missing alt text
- [ ] Check for oversized images impacting performance
- [ ] Update seasonal/promotional images
- [ ] Replace low-quality images
- [ ] Verify all images are indexed (Search Console)

---

## Image SEO Impact

### How Images Affect SEO

1. **Page Speed:** Optimized images improve Core Web Vitals
2. **Image Search:** Proper optimization can drive traffic from Google Images
3. **Rich Results:** Images enhance product rich snippets
4. **User Experience:** Quality images reduce bounce rate
5. **Social Sharing:** Open Graph images improve click-through

### Key Metrics to Monitor

- Largest Contentful Paint (LCP) - affected by image loading
- Cumulative Layout Shift (CLS) - prevented by setting dimensions
- Image search traffic in Google Search Console
- Page load time in Google Analytics

---

## Quick Reference Card

### File Naming
```
[brand]-[product]-[spec]-[view].webp
```

### Alt Text
```
[Brand] [Product Name] [Key Spec] - [View/Description]
```

### Dimensions
- Products: 2048x2048px (1:1)
- Thumbnails: 600x600px (1:1)
- Banners: 1920x600px

### File Sizes
- Products: < 300KB
- Thumbnails: < 50KB
- Banners: < 400KB

### Formats
- Preferred: WebP
- Fallback: JPEG (photos), PNG (transparency)
