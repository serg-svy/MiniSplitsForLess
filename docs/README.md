# MiniSplitsForLess SEO Documentation

Comprehensive SEO documentation for the MiniSplitsForLess HVAC e-commerce Shopify store.

## Table of Contents

1. [JSON-LD Structured Data Schemas](#json-ld-structured-data-schemas)
2. [Shopify Liquid Snippets](#shopify-liquid-snippets)
3. [SEO Guidelines](#seo-guidelines)
4. [Technical SEO](#technical-seo)

---

## JSON-LD Structured Data Schemas

Located in `/docs/json-ld-schemas/`:

| Schema | Description | File |
|--------|-------------|------|
| Product | Rich product information for search engines | [product-schema.json](./json-ld-schemas/product-schema.json) |
| FAQ | Frequently asked questions schema | [faq-schema.json](./json-ld-schemas/faq-schema.json) |
| Q&A | Question and Answer schema for product Q&A | [qa-schema.json](./json-ld-schemas/qa-schema.json) |
| Review | Product reviews and ratings | [review-schema.json](./json-ld-schemas/review-schema.json) |
| BreadcrumbList | Navigation breadcrumb schema | [breadcrumb-schema.json](./json-ld-schemas/breadcrumb-schema.json) |
| Organization | Business and brand information | [organization-schema.json](./json-ld-schemas/organization-schema.json) |
| LocalBusiness | Local business information (if applicable) | [local-business-schema.json](./json-ld-schemas/local-business-schema.json) |

---

## Shopify Liquid Snippets

Located in `/docs/shopify-liquid/`:

| Snippet | Description | File |
|---------|-------------|------|
| Product Page Schema | Complete product structured data | [product-jsonld.liquid](./shopify-liquid/product-jsonld.liquid) |
| Collection Schema | Collection page structured data | [collection-jsonld.liquid](./shopify-liquid/collection-jsonld.liquid) |
| Breadcrumb Schema | Breadcrumb navigation schema | [breadcrumb-jsonld.liquid](./shopify-liquid/breadcrumb-jsonld.liquid) |
| FAQ Page Schema | FAQ structured data for product pages | [faq-jsonld.liquid](./shopify-liquid/faq-jsonld.liquid) |
| Organization Schema | Global organization schema | [organization-jsonld.liquid](./shopify-liquid/organization-jsonld.liquid) |
| Review Schema | Product reviews structured data | [review-jsonld.liquid](./shopify-liquid/review-jsonld.liquid) |

---

## SEO Guidelines

Located in `/docs/seo-guidelines/`:

| Document | Description | File |
|----------|-------------|------|
| SEO Best Practices | Complete SEO checklist and guidelines | [seo-best-practices.md](./seo-guidelines/seo-best-practices.md) |
| Image Optimization | Image metadata and optimization guide | [image-optimization.md](./seo-guidelines/image-optimization.md) |
| On-Page SEO | Title tags, meta descriptions, headers | [on-page-seo.md](./seo-guidelines/on-page-seo.md) |
| Technical SEO | Site speed, mobile, Core Web Vitals | [technical-seo.md](./seo-guidelines/technical-seo.md) |

---

## Technical SEO

Located in `/docs/`:

| File | Description |
|------|-------------|
| [robots.txt](./robots.txt) | Search engine crawler directives |
| [sitemap-example.xml](./sitemap-example.xml) | XML sitemap structure example |

---

## Quick Start

### 1. Implement JSON-LD Schemas

Add the Liquid snippets to your Shopify theme:

```liquid
{% comment %}
  Add to theme.liquid or product.liquid
{% endcomment %}
{% render 'product-jsonld' %}
{% render 'breadcrumb-jsonld' %}
{% render 'organization-jsonld' %}
```

### 2. Validate Structured Data

Use these tools to validate your implementation:

- [Google Rich Results Test](https://search.google.com/test/rich-results)
- [Schema.org Validator](https://validator.schema.org/)
- [Google Search Console](https://search.google.com/search-console)

### 3. Monitor Performance

- Track rich result impressions in Google Search Console
- Monitor Core Web Vitals scores
- Review structured data errors and warnings

---

## HVAC Industry-Specific Considerations

### Product Categories for Mini Split Systems

- Single-Zone Mini Split Systems
- Multi-Zone Mini Split Systems
- Ductless AC Units
- Heat Pumps
- Commercial HVAC Units
- Accessories & Parts

### Key Product Attributes for SEO

- BTU Rating
- SEER Rating (Energy Efficiency)
- Coverage Area (sq ft)
- Heating/Cooling Capacity
- Voltage Requirements
- Warranty Information
- Brand (Cooper & Hunter, OLMO, etc.)

### Target Keywords Examples

- "ductless mini split system"
- "12000 BTU mini split"
- "multi-zone mini split"
- "Cooper Hunter mini split"
- "energy efficient AC"
- "wall mounted air conditioner"

---

## Contributing

When updating SEO documentation:

1. Test all JSON-LD schemas with Google's validator
2. Ensure Liquid snippets are compatible with Shopify 2.0 themes
3. Update examples with real product data when possible
4. Document any theme-specific customizations

---

## Resources

- [Schema.org](https://schema.org/)
- [Google Search Central](https://developers.google.com/search)
- [Shopify SEO Best Practices](https://www.shopify.com/blog/seo-for-shopify)
- [Core Web Vitals](https://web.dev/vitals/)
