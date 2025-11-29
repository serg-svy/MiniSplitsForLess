# On-Page SEO Guide for MiniSplitsForLess

Detailed guidelines for optimizing individual pages for search engines.

## Table of Contents

1. [Title Tags](#title-tags)
2. [Meta Descriptions](#meta-descriptions)
3. [Header Tags](#header-tags)
4. [URL Structure](#url-structure)
5. [Content Optimization](#content-optimization)
6. [Internal Linking](#internal-linking)
7. [Page-Type Templates](#page-type-templates)
8. [Shopify Implementation](#shopify-implementation)

---

## Title Tags

### Format Guidelines

**Product Pages:**
```
[Product Name] - [Key Spec] | MiniSplitsForLess
```

**Collection Pages:**
```
[Collection Name] - [Year/Descriptor] | MiniSplitsForLess
```

**Blog Posts:**
```
[Post Title] - [Topic Category] | MiniSplitsForLess
```

### Character Limits

- **Optimal Length:** 50-60 characters
- **Maximum Display:** ~60 characters before truncation
- **Include Brand:** Always at the end

### Examples by Page Type

#### Product Pages
| Good ✅ | Characters |
|---------|------------|
| Cooper & Hunter 12000 BTU Mini Split AC \| MiniSplitsForLess | 57 |
| OLMO 18K BTU Multi-Zone Heat Pump \| MiniSplitsForLess | 53 |
| 24000 BTU Ductless AC with WiFi \| MiniSplitsForLess | 50 |

| Bad ❌ | Issue |
|--------|-------|
| Mini Split | Too generic, no brand |
| Cooper & Hunter 12000 BTU Mini Split AC with Heat Pump and WiFi Control - Free Shipping | Too long, truncated |
| BUY NOW!!! Mini Split BEST PRICE | Spammy, no value |

#### Collection Pages
| Good ✅ | Characters |
|---------|------------|
| Single-Zone Mini Split Systems 2024 \| MiniSplitsForLess | 54 |
| Multi-Zone Ductless AC Units \| MiniSplitsForLess | 47 |
| Cooper & Hunter Mini Splits \| MiniSplitsForLess | 47 |

### Shopify Liquid Implementation

```liquid
{% comment %} In theme.liquid <head> section {% endcomment %}

<title>
  {%- if template == 'index' -%}
    {{ shop.name }} - Ductless Mini Split Systems | Free Shipping
  {%- elsif template contains 'product' -%}
    {{ product.title }} | {{ shop.name }}
  {%- elsif template contains 'collection' -%}
    {{ collection.title }} | {{ shop.name }}
  {%- elsif template contains 'article' -%}
    {{ article.title }} | {{ shop.name }}
  {%- elsif template contains 'page' -%}
    {{ page.title }} | {{ shop.name }}
  {%- elsif template == 'search' -%}
    Search Results | {{ shop.name }}
  {%- elsif template == 'cart' -%}
    Shopping Cart | {{ shop.name }}
  {%- else -%}
    {{ page_title }} | {{ shop.name }}
  {%- endif -%}
</title>
```

---

## Meta Descriptions

### Format Guidelines

**Structure:**
```
[What the page offers] + [Key benefits/specs] + [Call-to-action]
```

### Character Limits

- **Optimal Length:** 150-160 characters
- **Minimum Useful:** 120 characters
- **Maximum Display:** ~160 characters

### Examples by Page Type

#### Product Pages

**Example 1:**
```
Shop the Cooper & Hunter 12000 BTU mini split with SEER 22 efficiency. 
Covers 400-550 sq ft. Free shipping & 5-year warranty. Buy now!
```
(158 characters)

**Example 2:**
```
OLMO 18000 BTU ductless mini split with heat pump. Energy Star certified, 
WiFi control, whisper-quiet operation. Free nationwide shipping.
```
(156 characters)

#### Collection Pages

**Example:**
```
Browse our selection of single-zone mini split systems from 9,000-36,000 BTU. 
Cooper & Hunter, OLMO brands. Free shipping on all orders!
```
(152 characters)

#### Homepage

**Example:**
```
MiniSplitsForLess - USA's top online HVAC retailer. Shop ductless mini split AC 
and heat pumps. Free nationwide shipping. Cooper & Hunter, OLMO.
```
(159 characters)

### Elements to Include

| Page Type | Must Include |
|-----------|--------------|
| Product | Product name, key spec (BTU), benefit, CTA |
| Collection | Category name, brands available, value prop |
| Homepage | Business type, main products, USP |
| Blog | Topic summary, target audience, benefit |

### Shopify Implementation

```liquid
{% comment %} Meta description in theme.liquid {% endcomment %}

{%- capture meta_description -%}
  {%- if template contains 'product' -%}
    {{ product.description | strip_html | truncate: 155 }}
  {%- elsif template contains 'collection' -%}
    {%- if collection.description != blank -%}
      {{ collection.description | strip_html | truncate: 155 }}
    {%- else -%}
      Shop {{ collection.title }} at MiniSplitsForLess. Free nationwide shipping on all orders. Quality HVAC products from top brands.
    {%- endif -%}
  {%- elsif template contains 'article' -%}
    {{ article.excerpt | default: article.content | strip_html | truncate: 155 }}
  {%- elsif template contains 'page' -%}
    {{ page.content | strip_html | truncate: 155 }}
  {%- else -%}
    {{ shop.description | truncate: 155 }}
  {%- endif -%}
{%- endcapture -%}

<meta name="description" content="{{ meta_description | strip_newlines }}">
```

---

## Header Tags

### Hierarchy Structure

```
H1 - Main Page Title (ONE per page)
├── H2 - Major Section
│   ├── H3 - Subsection
│   └── H3 - Subsection
├── H2 - Major Section
│   ├── H3 - Subsection
│   │   ├── H4 - Detail
│   │   └── H4 - Detail
│   └── H3 - Subsection
└── H2 - Major Section
```

### H1 Guidelines

- **Only ONE H1 per page**
- Include primary keyword
- Match user search intent
- Keep under 60 characters
- Should match/relate to title tag

### Examples by Page Type

#### Product Page
```html
<h1>Cooper & Hunter 12000 BTU Mini Split Air Conditioner</h1>
<h2>Product Features</h2>
<h3>Cooling Performance</h3>
<h3>Energy Efficiency</h3>
<h2>Technical Specifications</h2>
<h2>Customer Reviews</h2>
<h2>Frequently Asked Questions</h2>
```

#### Collection Page
```html
<h1>Single-Zone Mini Split Systems</h1>
<h2>Browse by BTU Capacity</h2>
<h3>9,000 BTU Mini Splits</h3>
<h3>12,000 BTU Mini Splits</h3>
<h3>18,000 BTU Mini Splits</h3>
<h2>Shop by Brand</h2>
<h2>Buying Guide: Choosing the Right Size</h2>
```

#### Blog Post
```html
<h1>How to Choose the Right Mini Split Size for Your Room</h1>
<h2>Understanding BTU Ratings</h2>
<h3>What is a BTU?</h3>
<h3>BTU Calculator</h3>
<h2>Room Size Guidelines</h2>
<h3>Small Rooms (150-350 sq ft)</h3>
<h3>Medium Rooms (350-550 sq ft)</h3>
<h3>Large Rooms (550-800 sq ft)</h3>
<h2>Other Factors to Consider</h2>
<h3>Ceiling Height</h3>
<h3>Sun Exposure</h3>
<h3>Climate Zone</h3>
<h2>Conclusion</h2>
```

---

## URL Structure

### Best Practices

| Practice | Example |
|----------|---------|
| Use hyphens | `/cooper-hunter-mini-split` |
| Lowercase only | `/products/mini-split-12000-btu` |
| Keep short | `/collections/single-zone` |
| Include keywords | `/products/ductless-ac-unit` |
| Avoid parameters | `/products/...` not `/products?id=123` |
| No stop words | `/mini-split-installation` not `/the-mini-split-installation-guide` |

### URL Templates

**Products:**
```
/products/[brand]-[product-type]-[key-spec]
```
Examples:
- `/products/cooper-hunter-12000-btu-mini-split`
- `/products/olmo-multi-zone-heat-pump-3-zone`

**Collections:**
```
/collections/[category-name]
```
Examples:
- `/collections/single-zone-mini-splits`
- `/collections/cooper-hunter`
- `/collections/18000-btu`

**Blog Posts:**
```
/blogs/[blog-name]/[post-title]
```
Examples:
- `/blogs/hvac-guide/how-to-choose-mini-split-size`
- `/blogs/hvac-guide/seer-rating-explained`

---

## Content Optimization

### Keyword Placement

**Priority Locations:**
1. Title tag (near beginning)
2. H1 heading
3. First 100 words of content
4. H2/H3 subheadings
5. Image alt text
6. URL slug
7. Meta description

### Keyword Density

- **Primary keyword:** 1-2% of content
- **Secondary keywords:** 0.5-1% each
- **LSI keywords:** Use naturally throughout

### Content Length Guidelines

| Page Type | Minimum | Recommended | Maximum |
|-----------|---------|-------------|---------|
| Product Description | 300 words | 500-800 words | 1,500 words |
| Collection Description | 150 words | 300-500 words | 800 words |
| Blog Post | 800 words | 1,500-2,500 words | 4,000 words |
| FAQ Page | 500 words | 1,000-2,000 words | 3,000 words |

### Content Quality Checklist

- [ ] Answers user's search intent
- [ ] Includes primary keyword naturally
- [ ] Uses related keywords and synonyms
- [ ] Has clear, scannable structure
- [ ] Includes relevant images with alt text
- [ ] Links to related internal pages
- [ ] Provides unique value (not copied)
- [ ] Is factually accurate
- [ ] Updated regularly (for evergreen content)

---

## Internal Linking

### Best Practices

1. **Use Descriptive Anchor Text**
   - ✅ "View our [12000 BTU mini split collection](/collections/12000-btu)"
   - ❌ "[Click here](/collections/12000-btu) for 12000 BTU units"

2. **Link to Related Products**
   - Similar BTU ratings
   - Same brand
   - Accessories/parts

3. **Link to Supporting Content**
   - Buying guides
   - Installation instructions
   - FAQ pages

4. **Maintain Reasonable Link Counts**
   - 3-5 internal links per product page
   - 5-10 internal links per blog post
   - Don't overlink

### Internal Link Structure

```
Homepage
├── Collection Pages (link from nav, homepage)
│   ├── Product Pages (link from collections)
│   │   └── Related Products (link from product)
│   └── Category Guides (link from collection descriptions)
├── Blog Posts (link to products, collections)
└── Info Pages (link where relevant)
```

### Shopify Liquid for Related Products

```liquid
{% comment %} Related products section {% endcomment %}
<div class="related-products">
  <h2>You May Also Like</h2>
  {% assign related = collections[product.type].products | where_exp: 'p', 'p.id != product.id' %}
  {% for related_product in related limit: 4 %}
    <a href="{{ related_product.url }}">
      {{ related_product.title }}
    </a>
  {% endfor %}
</div>
```

---

## Page-Type Templates

### Product Page Template

```markdown
# [Product Name]

[Hero image with alt text]

## Overview
[2-3 sentences introducing the product, primary keyword in first sentence]

## Key Features
- [Feature 1 with benefit]
- [Feature 2 with benefit]
- [Feature 3 with benefit]
- [Feature 4 with benefit]

## Specifications
| Spec | Value |
|------|-------|
| BTU Rating | [Value] |
| SEER Rating | [Value] |
| Coverage Area | [Value] |
| ... | ... |

## What's Included
- [Item 1]
- [Item 2]
- [Item 3]

## Installation
[Brief installation overview with link to installation guide]

## Warranty Information
[Warranty details]

## Customer Reviews
[Reviews section]

## Frequently Asked Questions
[FAQ schema content]

## Related Products
[Link to related products]
```

### Collection Page Template

```markdown
# [Collection Name]

[Collection banner image]

## [Introduction - 100-150 words]
[Description of collection, who it's for, key benefits]

## Browse by [Filter Type]
[Subcategory links or filter options]

## Why Choose [Category]?
### [Benefit 1]
[Description]

### [Benefit 2]
[Description]

## How to Choose the Right [Product]
[Buying guidance - link to detailed guide]

## [Product Grid]
[Products with proper schema]

## Still Have Questions?
[CTA to contact or FAQ]
```

---

## Shopify Implementation

### Complete Head Section

```liquid
{% comment %} Complete SEO-optimized head section {% endcomment %}

<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  
  {% comment %} Title Tag {% endcomment %}
  <title>
    {%- if template == 'index' -%}
      {{ shop.name }} - Ductless Mini Split Systems | Free Shipping USA
    {%- elsif template contains 'product' -%}
      {{ product.title }} | {{ shop.name }}
    {%- elsif template contains 'collection' -%}
      {{ collection.title }} | {{ shop.name }}
    {%- elsif template contains 'article' -%}
      {{ article.title }} | {{ shop.name }} Blog
    {%- elsif template contains 'page' -%}
      {{ page.title }} | {{ shop.name }}
    {%- elsif template == 'search' -%}
      Search Results for "{{ search.terms }}" | {{ shop.name }}
    {%- else -%}
      {{ page_title }} | {{ shop.name }}
    {%- endif -%}
  </title>
  
  {% comment %} Meta Description {% endcomment %}
  {%- capture seo_description -%}
    {%- if template contains 'product' -%}
      Shop {{ product.title }} at {{ shop.name }}. {{ product.description | strip_html | truncate: 120 }} Free shipping!
    {%- elsif template contains 'collection' and collection.description != blank -%}
      {{ collection.description | strip_html | truncate: 155 }}
    {%- elsif template contains 'article' -%}
      {{ article.excerpt | default: article.content | strip_html | truncate: 155 }}
    {%- elsif template contains 'page' and page.content != blank -%}
      {{ page.content | strip_html | truncate: 155 }}
    {%- else -%}
      {{ shop.description | default: 'Shop ductless mini split systems and HVAC equipment. Free nationwide shipping. Cooper & Hunter, OLMO brands.' | truncate: 155 }}
    {%- endif -%}
  {%- endcapture -%}
  <meta name="description" content="{{ seo_description | strip_newlines | escape }}">
  
  {% comment %} Canonical URL {% endcomment %}
  <link rel="canonical" href="{{ canonical_url }}">
  
  {% comment %} Open Graph {% endcomment %}
  <meta property="og:site_name" content="{{ shop.name }}">
  <meta property="og:url" content="{{ canonical_url }}">
  <meta property="og:title" content="{{ page_title }}">
  <meta property="og:description" content="{{ seo_description | strip_newlines | escape }}">
  {%- if template contains 'product' -%}
    <meta property="og:type" content="product">
    <meta property="og:image" content="{{ product.featured_image | image_url: width: 1200 }}">
    <meta property="product:price:amount" content="{{ product.price | money_without_currency }}">
    <meta property="product:price:currency" content="{{ cart.currency.iso_code }}">
  {%- elsif template contains 'article' and article.image -%}
    <meta property="og:type" content="article">
    <meta property="og:image" content="{{ article.image | image_url: width: 1200 }}">
  {%- else -%}
    <meta property="og:type" content="website">
  {%- endif -%}
  
  {% comment %} Twitter Card {% endcomment %}
  <meta name="twitter:card" content="summary_large_image">
  <meta name="twitter:title" content="{{ page_title }}">
  <meta name="twitter:description" content="{{ seo_description | strip_newlines | escape }}">
  
  {% comment %} Structured Data {% endcomment %}
  {% render 'organization-jsonld' %}
  {% render 'breadcrumb-jsonld' %}
  {%- if template contains 'product' -%}
    {% render 'product-jsonld' %}
  {%- endif -%}
  {%- if template contains 'collection' -%}
    {% render 'collection-jsonld' %}
  {%- endif -%}
  
  {{ content_for_header }}
</head>
```

---

## On-Page SEO Checklist

### Pre-Launch
- [ ] Title tag is unique and under 60 characters
- [ ] Meta description is compelling and under 160 characters
- [ ] H1 contains primary keyword
- [ ] URL is clean and descriptive
- [ ] Content is unique and valuable
- [ ] Images have descriptive alt text
- [ ] Internal links are in place
- [ ] Structured data is implemented
- [ ] Page loads in under 3 seconds

### Post-Launch
- [ ] Page is indexed (check Search Console)
- [ ] No crawl errors
- [ ] Structured data is validated
- [ ] Ranking for target keywords
- [ ] No duplicate content issues
