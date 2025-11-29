# Technical SEO Guide for MiniSplitsForLess

Advanced technical SEO guidelines for optimal search performance.

## Table of Contents

1. [Core Web Vitals](#core-web-vitals)
2. [Site Speed Optimization](#site-speed-optimization)
3. [Mobile Optimization](#mobile-optimization)
4. [Crawlability & Indexation](#crawlability--indexation)
5. [XML Sitemaps](#xml-sitemaps)
6. [Robots.txt Configuration](#robotstxt-configuration)
7. [HTTPS & Security](#https--security)
8. [Shopify-Specific Technical SEO](#shopify-specific-technical-seo)

---

## Core Web Vitals

### Overview

Core Web Vitals are Google's metrics for measuring user experience:

| Metric | What It Measures | Target |
|--------|------------------|--------|
| LCP (Largest Contentful Paint) | Loading performance | ≤ 2.5 seconds |
| INP (Interaction to Next Paint) | Interactivity/Responsiveness | ≤ 200 milliseconds |
| CLS (Cumulative Layout Shift) | Visual stability | ≤ 0.1 |

> **Note:** INP (Interaction to Next Paint) replaced FID (First Input Delay) as the primary interactivity metric in March 2024. FID is now considered a legacy metric.

### Measuring Core Web Vitals

**Tools:**
- [Google PageSpeed Insights](https://pagespeed.web.dev/)
- [Google Search Console](https://search.google.com/search-console)
- [Chrome DevTools](https://developer.chrome.com/docs/devtools/)
- [Web Vitals Chrome Extension](https://chrome.google.com/webstore/detail/web-vitals/)
- [Lighthouse](https://developers.google.com/web/tools/lighthouse)

### Improving LCP (Largest Contentful Paint)

**Common Issues:**
- Slow server response time
- Render-blocking JavaScript and CSS
- Slow resource load times
- Client-side rendering

**Solutions:**
```liquid
{% comment %} Preload critical images {% endcomment %}
<link rel="preload" as="image" href="{{ product.featured_image | image_url: width: 800 }}">

{% comment %} Use responsive images with srcset {% endcomment %}
<img 
  src="{{ product.featured_image | image_url: width: 800 }}"
  srcset="
    {{ product.featured_image | image_url: width: 400 }} 400w,
    {{ product.featured_image | image_url: width: 800 }} 800w,
    {{ product.featured_image | image_url: width: 1200 }} 1200w
  "
  sizes="(max-width: 600px) 100vw, 50vw"
  alt="{{ product.featured_image.alt | escape }}"
  loading="eager"
  fetchpriority="high"
>
```

### Improving INP (Interaction to Next Paint)

**Common Issues:**
- Heavy JavaScript execution
- Long tasks blocking main thread
- Third-party scripts
- Slow event handlers

**Solutions:**
```html
<!-- Defer non-critical JavaScript -->
<script src="analytics.js" defer></script>

<!-- Load third-party scripts asynchronously -->
<script async src="https://third-party-script.js"></script>

<!-- Use web workers for heavy computation -->
<script type="module">
  if ('Worker' in window) {
    const worker = new Worker('/workers/heavy-task.js');
  }
</script>
```

### Improving CLS (Visual Stability)

**Common Issues:**
- Images without dimensions
- Ads/embeds without reserved space
- Dynamically injected content
- Web fonts causing FOIT/FOUT

**Solutions:**
```html
<!-- Always include width and height on images -->
<img 
  src="image.webp" 
  alt="Product image"
  width="800" 
  height="600"
  style="aspect-ratio: 4/3;"
>

<!-- Reserve space for dynamic content -->
<div class="ad-container" style="min-height: 250px;">
  <!-- Ad content loads here -->
</div>

<!-- Preload fonts to prevent layout shift -->
<link rel="preload" href="/fonts/main.woff2" as="font" type="font/woff2" crossorigin>
```

---

## Site Speed Optimization

### Image Optimization

**Checklist:**
- [ ] Use WebP format for all images
- [ ] Implement responsive images with srcset
- [ ] Lazy load below-fold images
- [ ] Compress images to optimal file sizes
- [ ] Use appropriate image dimensions

**Shopify Liquid Example:**
```liquid
{% comment %} Optimized product image {% endcomment %}
<picture>
  <source 
    media="(min-width: 1200px)"
    srcset="{{ image | image_url: width: 1200, format: 'webp' }}"
    type="image/webp"
  >
  <source 
    media="(min-width: 768px)"
    srcset="{{ image | image_url: width: 800, format: 'webp' }}"
    type="image/webp"
  >
  <img 
    src="{{ image | image_url: width: 600 }}"
    alt="{{ image.alt | escape }}"
    loading="lazy"
    decoding="async"
    width="{{ image.width }}"
    height="{{ image.height }}"
  >
</picture>
```

### CSS Optimization

**Best Practices:**
- Minimize CSS file size
- Inline critical CSS
- Remove unused CSS
- Use CSS containment

```html
<!-- Inline critical CSS -->
<style>
  /* Critical above-the-fold CSS */
  .header { /* ... */ }
  .hero { /* ... */ }
</style>

<!-- Load non-critical CSS asynchronously -->
<link rel="preload" href="/css/non-critical.css" as="style" onload="this.rel='stylesheet'">
<noscript><link rel="stylesheet" href="/css/non-critical.css"></noscript>
```

### JavaScript Optimization

**Best Practices:**
- Minimize and bundle JavaScript
- Defer non-critical scripts
- Remove unused JavaScript
- Code split for better loading

```liquid
{% comment %} Defer non-critical scripts {% endcomment %}
<script src="{{ 'theme.js' | asset_url }}" defer></script>

{% comment %} Load scripts conditionally {% endcomment %}
{% if template contains 'product' %}
  <script src="{{ 'product.js' | asset_url }}" defer></script>
{% endif %}
```

### Browser Caching

**Shopify handles caching automatically, but for custom assets:**

```liquid
{% comment %} Use asset_url which includes cache-busting {% endcomment %}
<link href="{{ 'theme.css' | asset_url }}" rel="stylesheet">
<script src="{{ 'theme.js' | asset_url }}" defer></script>
```

---

## Mobile Optimization

### Mobile-First Design

**Requirements:**
- [ ] Responsive design works on all screen sizes
- [ ] Touch targets are at least 48x48px
- [ ] Font size is at least 16px
- [ ] No horizontal scrolling
- [ ] Content doesn't overflow viewport

### Mobile SEO Checklist

- [ ] Mobile-friendly test passes
- [ ] Same content on mobile and desktop
- [ ] Fast loading on 3G/4G connections
- [ ] Easy navigation on mobile
- [ ] Forms are mobile-optimized

### Viewport Configuration

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

### Touch-Friendly Elements

```css
/* Minimum touch target size */
.button, 
.link, 
.tap-target {
  min-height: 48px;
  min-width: 48px;
  padding: 12px;
}

/* Adequate spacing between touch targets */
.nav-links a {
  padding: 12px 16px;
  margin: 4px 0;
}
```

---

## Crawlability & Indexation

### Ensuring Crawlability

**Checklist:**
- [ ] robots.txt doesn't block important content
- [ ] No "noindex" on pages you want indexed
- [ ] Internal links to all important pages
- [ ] No broken links (4xx errors)
- [ ] Proper redirect chains

### Canonical URLs

```liquid
{% comment %} Proper canonical URL implementation {% endcomment %}
<link rel="canonical" href="{{ canonical_url }}">

{% comment %} For paginated collections {% endcomment %}
{% if current_page == 1 %}
  <link rel="canonical" href="{{ collection.url }}">
{% else %}
  <link rel="canonical" href="{{ collection.url }}?page={{ current_page }}">
{% endif %}
```

### Pagination

```liquid
{% comment %} Pagination for collections {% endcomment %}
{% if paginate.previous %}
  <link rel="prev" href="{{ paginate.previous.url }}">
{% endif %}
{% if paginate.next %}
  <link rel="next" href="{{ paginate.next.url }}">
{% endif %}
```

### Handling Duplicate Content

**Common Shopify Duplicates:**
- `/collections/*/products/*` vs `/products/*`
- URL parameters (sorting, filtering)
- Pagination

**Solutions:**
```liquid
{% comment %} Canonical to main product URL {% endcomment %}
{% if template contains 'product' %}
  <link rel="canonical" href="{{ shop.url }}{{ product.url }}">
{% endif %}

{% comment %} Handle collection product URLs {% endcomment %}
{% if request.path contains '/collections/' and request.path contains '/products/' %}
  <link rel="canonical" href="{{ shop.url }}/products/{{ product.handle }}">
{% endif %}
```

### Noindex Tags

```liquid
{% comment %} Noindex search and utility pages {% endcomment %}
{% if template == 'search' %}
  <meta name="robots" content="noindex, follow">
{% endif %}

{% if template == 'cart' %}
  <meta name="robots" content="noindex, nofollow">
{% endif %}

{% comment %} Noindex paginated pages beyond page 1 (optional strategy) {% endcomment %}
{% if current_page > 1 %}
  <meta name="robots" content="noindex, follow">
{% endif %}
```

---

## XML Sitemaps

### Shopify Automatic Sitemap

Shopify automatically generates a sitemap at:
```
https://your-store.myshopify.com/sitemap.xml
```

### Sitemap Contents

Shopify's sitemap includes:
- All published products
- All collections
- All pages
- All blog posts
- Product images

### Submitting Sitemap

1. Go to [Google Search Console](https://search.google.com/search-console)
2. Navigate to Sitemaps
3. Enter: `sitemap.xml`
4. Click Submit

### Monitoring Sitemap Status

Check Search Console for:
- Number of URLs discovered
- Number of URLs indexed
- Any errors or warnings

---

## Robots.txt Configuration

### Shopify Default Robots.txt

Shopify generates robots.txt automatically at `/robots.txt`

### Customizing Robots.txt

In Shopify, edit the `robots.txt.liquid` file in your theme:

```liquid
{% comment %} 
  Custom robots.txt for MiniSplitsForLess
  Located at: templates/robots.txt.liquid
{% endcomment %}

# MiniSplitsForLess Robots.txt

User-agent: *
# Allow all crawlers

# Disallow paths
Disallow: /admin
Disallow: /cart
Disallow: /orders
Disallow: /checkouts/
Disallow: /checkout
Disallow: /carts
Disallow: /account
Disallow: /*?*variant=
Disallow: /search
Disallow: /collections/*+*
Disallow: /collections/*%2B*
Disallow: /collections/*%2b*
Disallow: /*?*sort_by*
Disallow: /*?*filter.*
Disallow: /*?*page=*

# Allow CSS and JS
Allow: /*.css
Allow: /*.js
Allow: /*.jpg
Allow: /*.jpeg
Allow: /*.png
Allow: /*.webp
Allow: /*.gif
Allow: /*.svg

# Sitemap
Sitemap: {{ shop.url }}/sitemap.xml

# Crawl-delay (optional)
# Crawl-delay: 10
```

### Robots.txt Best Practices

| Do | Don't |
|----|-------|
| Block admin/checkout pages | Block product pages |
| Block filtered/sorted URLs | Block CSS/JS files |
| Include sitemap reference | Block image files |
| Allow main content pages | Use overly restrictive rules |

---

## HTTPS & Security

### SSL/TLS Configuration

Shopify includes free SSL certificates automatically.

**Verify HTTPS:**
- [ ] All pages load over HTTPS
- [ ] No mixed content warnings
- [ ] HTTP redirects to HTTPS
- [ ] HSTS header is set (Shopify default)

### Security Headers

Shopify sets many security headers by default. For additional security:

```liquid
{% comment %} Content Security Policy (if implementing custom) {% endcomment %}
{% comment %} Note: Be careful with CSP on Shopify due to third-party apps {% endcomment %}
```

### Checking Security

**Tools:**
- [SSL Labs](https://www.ssllabs.com/ssltest/)
- [Security Headers](https://securityheaders.com/)
- Chrome DevTools > Security tab

---

## Shopify-Specific Technical SEO

### Theme Speed Optimization

**Minimize Theme Assets:**
- Remove unused JavaScript
- Combine CSS files where possible
- Minimize liquid loops

**Example - Efficient Liquid:**
```liquid
{% comment %} Good: Using assign for repeated values {% endcomment %}
{% assign product_image = product.featured_image %}
{% assign product_url = product.url %}

<a href="{{ product_url }}">
  <img src="{{ product_image | image_url: width: 400 }}" alt="{{ product_image.alt }}">
</a>

{% comment %} Bad: Repeated object access {% endcomment %}
<a href="{{ product.url }}">
  <img src="{{ product.featured_image | image_url: width: 400 }}" alt="{{ product.featured_image.alt }}">
</a>
```

### App Impact on Performance

**Audit Third-Party Apps:**
- Review installed apps' impact on load time
- Remove unused apps
- Consider app alternatives with better performance
- Test with and without apps

**Testing App Impact:**
1. Disable apps one by one
2. Run PageSpeed Insights after each
3. Identify slowest apps
4. Consider alternatives or removal

### Shopify CDN Usage

Shopify automatically serves assets via CDN. Ensure you use:
```liquid
{{ 'file.css' | asset_url }}
{{ 'image.jpg' | file_url }}
{{ image | image_url: width: 800 }}
```

### Handling Variants

**Variant URL Structure:**
```
/products/product-name?variant=12345678
```

**SEO for Variants:**
```liquid
{% comment %} Canonical to main product URL {% endcomment %}
<link rel="canonical" href="{{ shop.url }}{{ product.url }}">

{% comment %} Or if variants should be indexed separately {% endcomment %}
{% if product.selected_variant %}
  <link rel="canonical" href="{{ shop.url }}{{ product.url }}?variant={{ product.selected_variant.id }}">
{% endif %}
```

---

## Technical SEO Audit Checklist

### Monthly Checks
- [ ] Review Google Search Console for errors
- [ ] Check Core Web Vitals report
- [ ] Monitor index coverage
- [ ] Review mobile usability report
- [ ] Check for security issues

### Quarterly Checks
- [ ] Full site crawl with Screaming Frog
- [ ] Review and update robots.txt
- [ ] Audit redirect chains
- [ ] Check for broken links
- [ ] Review structured data errors
- [ ] Analyze site speed trends

### Annual Review
- [ ] Complete technical SEO audit
- [ ] Review and optimize sitemap
- [ ] Update canonical strategy
- [ ] Evaluate CDN performance
- [ ] Review third-party script impact
- [ ] Update security configurations

---

## Monitoring Tools Setup

### Google Search Console

1. Verify site ownership
2. Submit sitemap
3. Set up email alerts
4. Review weekly for issues

### Google Analytics 4

1. Set up GA4 property
2. Configure e-commerce tracking
3. Set up Core Web Vitals monitoring
4. Create custom reports for SEO

### Recommended Alerts

- Index coverage issues
- Core Web Vitals failing
- Security issues detected
- Manual actions applied
- Significant traffic changes
