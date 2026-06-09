# Screenshot Inclusion Guide — InsectFlux Case Study

## Screenshots captured

The following screenshots were captured from the public InsectFlux website while logged out:

```text
assets/homepage-hero.png
assets/marketplace-products.png
assets/homepage-how-it-works.png
```

## Best screenshot to use first

Use `assets/homepage-hero.png` at the top of the case study because it is clean, branded, and does not expose customer data, internal data, orders, payments, or logged-in user information.

## Second screenshot

Use `assets/marketplace-products.png` to show that this was a real marketplace product, but review it before publishing because it displays:

- product names,
- product images,
- prices,
- stock labels,
- possible third-party brands,
- North American/CAD market positioning.

If any of that is sensitive, blur or remove this image before publishing.

## Third screenshot

Use `assets/homepage-how-it-works.png` as a safe supporting screenshot. It shows the product narrative without exposing operational data.

## Public-safety checklist before publishing

Before pushing the case study publicly, confirm:

- InsectFlux name/logo can be shown publicly.
- Public website screenshots are okay to reuse in a personal portfolio/case study.
- Product listings/prices/stock labels are okay to show.
- Third-party product images are okay to show, or are blurred/anonymized.
- No logged-in dashboard, private customer, supplier, order, payment, or admin data is visible.
- The case study does not imply sole ownership of the 3-person project.
- The case study does not expose private code or deployment details.

## How to add screenshots to GitHub README

Use relative Markdown paths:

```markdown
![InsectFlux homepage hero](assets/homepage-hero.png)
![InsectFlux marketplace products](assets/marketplace-products.png)
![InsectFlux how it works](assets/homepage-how-it-works.png)
```

If publishing as `mohamedswe/insectflux-case-study`, keep this structure:

```text
insectflux-case-study/
  README.md
  architecture.md
  linkedin-resume-snippets.md
  publish-checklist.md
  screenshot-guide.md
  assets/
    homepage-hero.png
    marketplace-products.png
    homepage-how-it-works.png
```

## If you want to sanitize images

Recommended edits:

- Blur product brand labels if permissions are unclear.
- Blur prices/stock counts if they are sensitive or likely to become outdated.
- Avoid logged-in views entirely.
- Prefer public marketing pages over internal dashboards.

You can do this with any image editor, or ask Hermes to generate sanitized copies.
