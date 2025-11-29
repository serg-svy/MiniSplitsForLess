# SEO Best Practices for MiniSplitsForLess

Comprehensive SEO guidelines for the HVAC e-commerce Shopify store.

## Table of Contents

1. [Technical SEO Checklist](#technical-seo-checklist)
2. [On-Page SEO](#on-page-seo)
3. [Product Page Optimization](#product-page-optimization)
4. [Collection Page Optimization](#collection-page-optimization)
5. [Content Strategy](#content-strategy)
6. [Link Building](#link-building)
7. [Local SEO](#local-seo)
8. [Monitoring & Analytics](#monitoring--analytics)

---

## Technical SEO Checklist

### Site Speed & Performance

- [ ] Optimize images (WebP format, lazy loading)
- [ ] Minimize CSS and JavaScript
- [ ] Enable browser caching
- [ ] Use a CDN (Shopify's built-in CDN)
- [ ] Reduce server response time
- [ ] Optimize Critical Rendering Path
- [ ] Target Core Web Vitals scores:
  - LCP (Largest Contentful Paint): < 2.5s
  - FID (First Input Delay): < 100ms
  - CLS (Cumulative Layout Shift): < 0.1

### Mobile Optimization

- [ ] Responsive design on all pages
- [ ] Touch-friendly navigation (48px+ tap targets)
- [ ] Readable font sizes (16px+ base)
- [ ] No horizontal scrolling
- [ ] Mobile-first indexing ready
- [ ] Test with Google Mobile-Friendly Test

### Crawlability & Indexation

- [ ] Submit XML sitemap to Google Search Console
- [ ] Configure robots.txt properly
- [ ] Implement canonical URLs on all pages
- [ ] Fix broken links (4xx errors)
- [ ] Resolve redirect chains
- [ ] Handle pagination with rel="next/prev" or load more
- [ ] Use hreflang tags if multi-language

### Structured Data

- [ ] Product schema on all product pages
- [ ] BreadcrumbList schema site-wide
- [ ] Organization schema on homepage
- [ ] FAQ schema on relevant pages
- [ ] Review/AggregateRating schema
- [ ] Validate with Google Rich Results Test

### Security & HTTPS

- [ ] SSL certificate active (Shopify default)
- [ ] No mixed content warnings
- [ ] Security headers configured

---

## On-Page SEO

### Title Tags

**Format:** `Primary Keyword - Secondary Keyword | Brand Name`

**Character Limit:** 50-60 characters

**Examples:**
- `12000 BTU Mini Split AC - Cooper & Hunter | MiniSplitsForLess`
- `Ductless Mini Split Systems - Free Shipping | MiniSplitsForLess`
- `Multi-Zone Mini Split - 2-5 Zones | MiniSplitsForLess`

**Best Practices:**
- Include primary keyword near the beginning
- Each page should have a unique title
- Include brand name at the end
- Avoid keyword stuffing

### Meta Descriptions

**Character Limit:** 150-160 characters

**Format:** Include primary keyword, value proposition, and call-to-action

**Examples:**
```
Shop the Cooper & Hunter 12000 BTU mini split AC with SEER 22 efficiency. 
Free shipping, 5-year warranty. Cool up to 550 sq ft. Buy now!
```

```
Browse our collection of ductless mini split systems. Energy-efficient 
heating & cooling from Cooper & Hunter and OLMO. Free nationwide shipping!
```

**Best Practices:**
- Unique description for every page
- Include primary keyword naturally
- Add a call-to-action (Shop now, Buy today, etc.)
- Highlight unique selling points (free shipping, warranty)

### Header Tags (H1-H6)

**Structure:**
```html
<h1>Main Page Title (One per page)</h1>
  <h2>Major Section</h2>
    <h3>Subsection</h3>
    <h3>Subsection</h3>
  <h2>Major Section</h2>
    <h3>Subsection</h3>
```

**Best Practices:**
- Only one H1 per page
- Include primary keyword in H1
- Use H2-H6 hierarchically
- Keep headers descriptive and scannable

### URL Structure

**Format:** `domain.com/collections/category-name/products/product-name`

**Best Practices:**
- Use hyphens, not underscores
- Keep URLs short and descriptive
- Include primary keyword
- Avoid parameters when possible
- Use lowercase letters only

**Examples:**
- ✅ `/products/cooper-hunter-12000-btu-mini-split`
- ❌ `/products/CH_12K_MS_Unit_2024_v2`

---

## Product Page Optimization

### Required Elements

1. **Unique Title Tag** with BTU, brand, and product type
2. **Meta Description** with key specs and value proposition
3. **H1 Heading** matching the product name
4. **High-Quality Images** with descriptive alt text
5. **Detailed Product Description** (300+ words)
6. **Technical Specifications Table**
7. **Customer Reviews** with schema markup
8. **FAQ Section** for common questions
9. **Breadcrumb Navigation**
10. **Related Products** section

### Product Description Template

```markdown
## [Product Name]

[Opening paragraph: What is this product and who is it for? 80-100 words]

### Key Features
- Feature 1 with benefit
- Feature 2 with benefit
- Feature 3 with benefit

### Specifications
| Specification | Value |
|---------------|-------|
| BTU Rating | 12,000 BTU |
| SEER Rating | 22 |
| Coverage Area | 400-550 sq ft |
| Voltage | 208-230V |

### What's Included
- Item 1
- Item 2
- Item 3

### Why Choose [Brand Name]?
[Benefits of the brand, 50-80 words]

### Warranty Information
[Warranty details]
```

### Image Optimization for Products

- **Main Image:** 1200x1200px minimum, white background
- **Alt Text:** `Cooper & Hunter 12000 BTU Mini Split Indoor Unit - White`
- **File Name:** `cooper-hunter-12000-btu-mini-split-indoor.webp`
- **Multiple Angles:** Front, side, installed, accessories
- **Lifestyle Images:** Product in use context

---

## Collection Page Optimization

### Collection Description Template

```markdown
# [Collection Name] - [Year]

[Introduction paragraph describing the collection and its benefits. 100-150 words. 
Include primary and secondary keywords naturally.]

## Why Choose Our [Category]?

### [Benefit 1]
[Description]

### [Benefit 2]
[Description]

## How to Choose the Right [Product Type]

[Buying guide content that helps customers make decisions. 200-300 words. 
Include internal links to related guides or products.]

## Popular [Category] Sizes

- **9,000 BTU** - Up to 350 sq ft
- **12,000 BTU** - 400-550 sq ft
- **18,000 BTU** - 550-700 sq ft
- **24,000 BTU** - 700-1,000 sq ft

[Closing paragraph with call-to-action]
```

### Collection Page Requirements

- [ ] Unique title tag with collection name
- [ ] Meta description highlighting collection
- [ ] H1 heading (collection title)
- [ ] 200-500 word collection description
- [ ] Product count displayed
- [ ] Filter options (price, BTU, brand, features)
- [ ] Sort functionality
- [ ] Pagination or infinite scroll
- [ ] Breadcrumb navigation

---

## Content Strategy

### Blog Topics for HVAC Industry

**Educational Content:**
- How to Choose the Right Mini Split Size
- Understanding SEER Ratings: A Complete Guide
- Single-Zone vs Multi-Zone: Which is Right for You?
- DIY vs Professional Mini Split Installation
- Mini Split Maintenance: Annual Checklist

**Product-Focused Content:**
- Cooper & Hunter vs OLMO: Brand Comparison
- Best Mini Splits for Bedrooms
- Top 10 Mini Splits for Garages
- Energy-Efficient Mini Splits Under $1000

**Seasonal Content:**
- Preparing Your Mini Split for Summer
- Winter Heat Pump Efficiency Tips
- Spring HVAC Maintenance Checklist

**Local Content:**
- Best Mini Splits for Florida Humidity
- Cold Climate Heat Pumps for Northern States
- Mini Split Sizing for Arizona Heat

### Content Guidelines

1. **Word Count:** 1,500-2,500 words for comprehensive guides
2. **Keyword Density:** 1-2% for primary keyword
3. **Internal Links:** 3-5 per article to products/collections
4. **External Links:** 1-2 to authoritative sources
5. **Images:** 3-5 relevant images with alt text
6. **Video:** Embed relevant videos when available
7. **Update Frequency:** Refresh evergreen content annually

---

## Link Building

### Internal Linking Strategy

- Link from blog posts to relevant products
- Link between related products
- Link from product pages to guides
- Use descriptive anchor text
- Create topic clusters around main categories

### External Link Opportunities

- HVAC industry publications
- Home improvement blogs
- Energy efficiency websites
- Local contractor partnerships
- Manufacturer relationships

---

## Local SEO

### Google Business Profile

- Claim and verify business listing
- Complete all business information
- Add products and services
- Respond to reviews
- Post updates regularly

### Local Keywords

- "mini split installation [city]"
- "HVAC store [state]"
- "buy mini split near me"

### NAP Consistency

Ensure Name, Address, Phone number are consistent across:
- Website footer
- Google Business Profile
- Social media profiles
- Local directories

---

## Monitoring & Analytics

### Key Metrics to Track

**Search Console:**
- Impressions and clicks
- Average position
- Click-through rate
- Index coverage
- Core Web Vitals

**Google Analytics:**
- Organic traffic
- Bounce rate by page
- Time on page
- Conversion rate
- Top landing pages

**Rank Tracking:**
- Primary keyword positions
- Brand keyword visibility
- Featured snippet opportunities
- Local pack rankings

### Monthly SEO Tasks

1. Review Search Console for errors
2. Check Core Web Vitals scores
3. Analyze top-performing pages
4. Update underperforming content
5. Build new internal links
6. Review and respond to reviews
7. Publish new blog content
8. Monitor competitor activity

### Quarterly SEO Audit

1. Full technical SEO audit
2. Content gap analysis
3. Backlink profile review
4. Keyword research refresh
5. Schema markup validation
6. Mobile usability check
7. Site speed analysis
8. Competitive analysis

---

## SEO Tools Recommended

### Free Tools
- Google Search Console
- Google Analytics
- Google PageSpeed Insights
- Google Mobile-Friendly Test
- Google Rich Results Test
- Bing Webmaster Tools

### Paid Tools (Optional)
- Ahrefs / SEMrush (keyword research, backlinks)
- Screaming Frog (technical audits)
- Surfer SEO (content optimization)
- Schema App (structured data management)

---

## Quick Reference: HVAC Keywords

### High-Volume Keywords
- mini split
- ductless mini split
- mini split air conditioner
- ductless AC
- mini split heat pump

### Long-Tail Keywords
- 12000 BTU mini split
- multi zone mini split system
- mini split with heat pump
- quiet mini split for bedroom
- energy efficient mini split

### Brand Keywords
- Cooper Hunter mini split
- OLMO mini split
- [brand] ductless AC

### Buyer Intent Keywords
- buy mini split online
- mini split free shipping
- best mini split 2024
- mini split sale
- cheap mini split system
