# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static website for CG & P Site Services Ltd (cgp-recruitment.co.uk) - a UK recruitment company. The site consists of a modern holding page with UK GDPR-compliant legal pages (Privacy Policy and Terms of Service).

**Key Context:**
- Company Registration: 15397387 (England and Wales)
- VAT Number: GB469567332
- ICO Registration: Pending addition to Privacy Policy (placeholder: `[TO BE ADDED]`)
- Jurisdiction: England and Wales
- Legal Framework: UK GDPR, Data Protection Act 2018, Consumer Rights Act 2015

## Architecture

### Site Structure
The website is a pure static HTML/CSS site with no build process:

```
index.html                    # Main holding page
CG&P-Privacy-Policy.html      # UK GDPR-compliant privacy policy
CG&P-Terms-of-Service.html    # UK legal terms of service
CG&P logo.jpg                 # Company logo (not in repo)
```

### Shared Design System

All three HTML files share an identical design language:
- **Color Palette:**
  - Background: Dark gradient (#0D0D0D to #1a1a1a at 135deg)
  - Brand Yellow: #f4d03f (headings, links, accents)
  - Text: #ddd (body), #ccc (secondary), #aaa (meta)
- **Typography:** Arial, sans-serif with 1.6-1.8 line-height
- **Animations:** 0.8s fadeIn (translateY 20px → 0) on page load
- **Responsive Breakpoints:** 768px (tablet), 480px (mobile)
- **Favicon:** SVG data URI with yellow "CG" text on dark background

### Legal Pages Architecture

Both legal pages (`CG&P-Privacy-Policy.html` and `CG&P-Terms-of-Service.html`) follow this structure:

1. **Company Info Box** (top): Highlighted box with company details, VAT, ICO number
2. **Main Content Sections**: Numbered sections with h2/h3 hierarchy
3. **Highlight Boxes**: Used for important info (ICO complaints, contact details)
4. **Contact Section**: Duplicate company info at bottom
5. **Disclaimer Footer**: Copyright with company number

**Important:** The Privacy Policy contains ICO registration number in TWO places (lines ~217 and ~443). Both must be updated together.

## UK Legal Compliance Requirements

### Privacy Policy Must Include:
- UK GDPR and Data Protection Act 2018 compliance
- Data subject rights (all 8 rights: access, rectification, erasure, restriction, portability, objection, automated decision-making, withdraw consent)
- Legal basis for processing (consent, contract, legal obligation, legitimate interests)
- ICO complaint procedures with full contact details
- Data retention schedules (specific timeframes for each category)
- International data transfer mechanisms (post-Brexit)
- Cookie policy integrated
- Company registration details (Companies House number)

### Terms of Service Must Include:
- England and Wales governing law and jurisdiction
- Consumer Rights Act 2015 acknowledgment
- Computer Misuse Act 1990 references
- Proper liability limitations (UK-compliant)
- Company registration details
- Clear statement about Scottish and Northern Irish consumer rights

## Common Tasks

### Updating Company Information

When updating company details, check these locations:

**Privacy Policy:**
- Line ~215: Company info box (top)
- Line ~440: Contact section (bottom)

**Terms of Service:**
- Line ~200: Company info box (top)
- Line ~347: Contact section (bottom)

### Adding ICO Registration Number

Replace `[TO BE ADDED]` in Privacy Policy only (2 occurrences):
```bash
# Search for placeholder
grep -n "\[TO BE ADDED\]" CG&P-Privacy-Policy.html

# Should appear on lines ~217 and ~443
```

### Maintaining Visual Consistency

When modifying any page:
1. Preserve the exact color values (#f4d03f, #0D0D0D, #1a1a1a, etc.)
2. Keep animation timing at 0.8s for fadeIn
3. Maintain responsive breakpoints at 768px and 480px
4. Ensure touch targets are minimum 44x44px (preferably 60x60px)
5. Use the same company info box styling (rgba(244, 208, 63, 0.1) background)

### Testing Legal Compliance

When updating legal pages:
1. Verify ICO contact details are current (https://ico.org.uk)
2. Ensure all data subject rights are listed (8 rights minimum)
3. Check jurisdiction language mentions Scotland and Northern Ireland options
4. Confirm effective dates are updated
5. Validate company numbers (Companies House, VAT, ICO) are consistent

## Deployment

This is a static site with no build process. To deploy:

1. Add ICO registration number if pending
2. Upload all HTML files to web server
3. Upload `CG&P logo.jpg` to same directory
4. Test all links and responsive behavior

**Pre-deployment checklist:** See `DEPLOYMENT-CHECKLIST.md`

## File Interdependencies

- `index.html` links to both legal pages (footer)
- Legal pages link back to `index.html` via "Back to Home" link
- Legal pages cross-reference each other (Privacy Policy mentions Cookie Policy; Terms mention Privacy Policy)
- All pages reference the same logo file
- All pages use the same inline favicon (SVG data URI)

## Critical Constraints

1. **No registered office address on website** - This was intentionally excluded
2. **ICO number has placeholder** - Awaiting customer to provide
3. **Static HTML only** - No JavaScript framework, no build process
4. **Inline CSS only** - All styles are embedded in `<style>` tags
5. **UK legal jurisdiction** - All legal language must comply with England and Wales law

## Design Patterns

### Responsive Touch Targets
```css
min-width: 44px;   /* WCAG minimum */
min-height: 44px;
width: 60px;       /* Actual default */
height: 60px;
```

### Hover Animations
```css
transition: all 0.3s ease;
transform: scale(1.15) translateY(-5px);  /* Hover */
transform: scale(1.05);                    /* Active */
```

### Company Info Box
```css
background-color: rgba(244, 208, 63, 0.1);
border-left: 4px solid #f4d03f;
padding: 20px;
border-radius: 5px;
```

## Important Notes

- Effective dates on legal pages: 15 December 2024 (update annually)
- Copyright year: 2025 (update annually)
- Font Awesome 6.0.0-beta3 used for social icons (index.html only)
- Mobile-first responsive design approach
- All external links use `target="_blank" rel="noopener"`
