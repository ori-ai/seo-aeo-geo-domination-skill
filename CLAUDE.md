# SKILL: SEO / AEO / GEO Domination Stack
# Every website built MUST comply with ALL requirements below.
# This is non-negotiable. No website ships without these elements.

---

## SECTION 1: FRAMEWORK & RENDERING (FOUNDATION)

Every website MUST be built with server-side rendering or static site generation. Client-side-only React apps are NEVER acceptable.

### Requirements:
- Use Next.js (App Router preferred) as the framework for EVERY project
- - Every page MUST export server-rendered HTML — no content behind client-side-only JavaScript
  - - Use Static Site Generation (SSG) with `generateStaticParams` for all static pages
    - - Use Server-Side Rendering (SSR) only for dynamic/personalized content
      - - Framer Motion animations MUST be wrapped in client components ("use client") but the underlying content MUST still be present in the server-rendered HTML
        - - NEVER hide meaningful text content inside JavaScript-only rendering
         
          - ---

          ## SECTION 2: TECHNICAL SEO (MANDATORY ON EVERY BUILD)

          ### 2.1 — Meta Tags (Every Page)
          Every page MUST include:
          - A unique `<title>` tag — keyword-rich, max 60 characters
          - - `<meta name="description">` — compelling with primary keyword, max 155 characters
            - - `<meta name="viewport" content="width=device-width, initial-scale=1">`
              - - `<meta name="robots" content="index, follow, max-image-preview:large, max-snippet:-1, max-video-preview:-1">`
                - - `<link rel="canonical">` with the full canonical URL
                 
                  - ### 2.2 — Open Graph & Social Meta (Every Page)
                  - Every page MUST include:
                  - - `og:title`, `og:description`, `og:image` (1200x630), `og:url`, `og:type`, `og:site_name`
                    - - `twitter:card` (summary_large_image), `twitter:title`, `twitter:description`, `twitter:image`
                     
                      - ### 2.3 — Semantic HTML Structure (Enforced)
                      - - ONE `<h1>` per page containing the primary keyword
                        - - Logical heading hierarchy: h1 then h2 then h3 (never skip levels)
                          - - Use `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<aside>`, `<footer>` — NEVER generic divs for layout landmarks
                            - - Every `<img>` MUST have a descriptive alt attribute (not empty, not "image")
                              - - Every `<a>` link MUST have descriptive anchor text (never "click here")
                                - - Use `<ul>` / `<ol>` for real lists
                                  - - Use `<time datetime="">` for any dates displayed
                                   
                                    - ### 2.4 — URL Structure
                                    - - All URLs MUST be lowercase, hyphenated, human-readable
                                      - - No trailing slashes (or be consistent — pick one pattern)
                                        - - No query parameters for page content (use clean paths)
                                          - - Example: /services/web-design NOT /page?id=3
                                           
                                            - ### 2.5 — Sitemap & Robots
                                            - Generate these files automatically at build time:
                                           
                                            - /sitemap.xml — Include ALL public pages with:
                                            - - `<loc>` full canonical URL
                                              - - `<lastmod>` accurate last modified date
                                                - - `<changefreq>` appropriate frequency
                                                  - - `<priority>` 1.0 for homepage, 0.8 for main pages, 0.6 for subpages
                                                   
                                                    - /robots.txt MUST contain:
                                                    - ```
                                                      User-agent: *
                                                      Allow: /
                                                      Sitemap: https://{domain}/sitemap.xml

                                                      User-agent: GPTBot
                                                      Allow: /

                                                      User-agent: ClaudeBot
                                                      Allow: /

                                                      User-agent: PerplexityBot
                                                      Allow: /

                                                      User-agent: Google-Extended
                                                      Allow: /
                                                      ```

                                                      IMPORTANT: NEVER block AI crawlers unless the client explicitly requests it.

                                                      ### 2.6 — Performance Requirements (Core Web Vitals)
                                                      Every site MUST be optimized for:
                                                      - LCP (Largest Contentful Paint): under 2.5 seconds
                                                      - - INP (Interaction to Next Paint): under 200ms
                                                        - - CLS (Cumulative Layout Shift): under 0.1
                                                         
                                                          - Implementation rules:
                                                          - - ALL images use Next.js Image component with proper width, height, sizes, and priority (for above-fold)
                                                            - - Use loading="lazy" for below-fold images
                                                              - - Use WebP/AVIF format via Next.js image optimization
                                                                - - Preload critical fonts with link rel="preload"
                                                                  - - Use next/font for font loading (zero layout shift)
                                                                    - - Minimize third-party scripts — defer or lazy-load non-critical JS
                                                                      - - CSS must be inlined or loaded with zero render-blocking
                                                                        - - Implement proper image sizes attribute for responsive serving
                                                                         
                                                                          - ---

                                                                          ## SECTION 3: AEO — ANSWER ENGINE OPTIMIZATION

                                                                          ### 3.1 — JSON-LD Structured Data (Required on EVERY site)
                                                                          Create a reusable SchemaMarkup component. Every site MUST include AT MINIMUM:

                                                                          Organization Schema (site-wide):
                                                                          - @type: Organization with name, url, logo, description, sameAs (social links), contactPoint
                                                                         
                                                                          - WebSite Schema (homepage):
                                                                          - - @type: WebSite with name, url, and SearchAction potentialAction
                                                                           
                                                                            - Add these schemas WHEN the content type exists:
                                                                            - - FAQPage — for ANY page with Q&A content
                                                                              - - HowTo — for ANY process/tutorial content
                                                                                - - Service — for each service offered
                                                                                  - - Product — for each product listed
                                                                                    - - LocalBusiness — if the business serves a physical area
                                                                                      - - BreadcrumbList — on EVERY page with breadcrumb navigation
                                                                                        - - Article / BlogPosting — for any blog/article pages
                                                                                          - - Review / AggregateRating — if reviews are displayed
                                                                                            - - Person — for team/about pages
                                                                                             
                                                                                              - ### 3.2 — FAQ Content Blocks
                                                                                              - Every site MUST include an FAQ section on the homepage or relevant service pages:
                                                                                              - - Minimum 5 questions
                                                                                                - - Each answer must be 2-4 sentences — concise, direct, factual
                                                                                                  - - Questions MUST use natural language (how people actually search/ask AI)
                                                                                                    - - Wrap in both visible HTML AND FAQPage JSON-LD schema
                                                                                                      - - First sentence of each answer must directly answer the question (no filler)
                                                                                                       
                                                                                                        - ### 3.3 — Content Structure for AI Extraction
                                                                                                        - - Every page MUST open with a clear, definitive statement of what the page is about (first 1-2 sentences)
                                                                                                          - - Use the inverted pyramid — most important info first
                                                                                                            - - Include specific numbers, statistics, and data points where possible
                                                                                                              - - Define key terms explicitly: "Term is definition" format
                                                                                                                - - Use short paragraphs (2-4 sentences max)
                                                                                                                 
                                                                                                                  - ---
                                                                                                                  
                                                                                                                  ## SECTION 4: GEO — GENERATIVE ENGINE OPTIMIZATION
                                                                                                                  
                                                                                                                  ### 4.1 — AI Crawler Accessibility
                                                                                                                  - robots.txt MUST allow all major AI crawlers (see Section 2.5)
                                                                                                                  - - Site MUST serve full HTML content without JavaScript execution required
                                                                                                                    - - All meaningful content MUST be in the DOM on initial server render
                                                                                                                      - - No content behind login walls, paywalls, or interstitials for public pages
                                                                                                                        - - Do NOT use noai or noimageai meta tags unless client explicitly requests
                                                                                                                         
                                                                                                                          - ### 4.2 — Entity & Brand Optimization
                                                                                                                          - - Use the EXACT brand name consistently across every page (no variations in first reference)
                                                                                                                            - - Include a comprehensive About page with:
                                                                                                                              -   - Brand story and mission
                                                                                                                                  -   - Team credentials and expertise
                                                                                                                                      -   - Years of experience / notable achievements
                                                                                                                                          -   - Industry affiliations or certifications
                                                                                                                                              - - Add Organization + Person schema for founders/key team members
                                                                                                                                                - - Link to authoritative external sources where relevant (builds trust signals)
                                                                                                                                                 
                                                                                                                                                  - ### 4.3 — E-E-A-T Signals (Experience, Expertise, Authority, Trust)
                                                                                                                                                  - Every site MUST include:
                                                                                                                                                  - - Experience: Case studies, portfolio items, or testimonials with specific details
                                                                                                                                                    - - Expertise: Credentials, certifications, or detailed knowledge demonstrations
                                                                                                                                                      - - Authority: External links received, mentions, or industry recognition
                                                                                                                                                        - - Trust: Privacy policy, terms of service, clear contact information, physical address if applicable, SSL (HTTPS enforced)
                                                                                                                                                         
                                                                                                                                                          - Implementation:
                                                                                                                                                          - - Create /privacy-policy and /terms-of-service pages (even if basic)
                                                                                                                                                            - - Footer MUST include: business name, contact email, phone (if provided), physical address (if applicable), copyright notice
                                                                                                                                                              - - Include social proof: testimonials, client logos, review ratings
                                                                                                                                                                - - Add author attribution to any blog/article content
                                                                                                                                                                 
                                                                                                                                                                  - ### 4.4 — Quotability & Citation Optimization
                                                                                                                                                                  - - Write at least 3-5 quotable statements per page — definitive, specific, cite-worthy sentences that AI models will want to reference
                                                                                                                                                                    - - Format: "Brand is specific claim with data" or "Topic involves clear factual explanation"
                                                                                                                                                                      - - Include original statistics, proprietary data, or unique insights when available
                                                                                                                                                                        - - Use blockquote for key pullout statements
                                                                                                                                                                          - - Bold key phrases that summarize sections (these become extraction targets)
                                                                                                                                                                           
                                                                                                                                                                            - ### 4.5 — Topical Authority Architecture
                                                                                                                                                                            - - Build content in topic clusters: one pillar page + multiple supporting pages
                                                                                                                                                                              - - Internal link from every supporting page to the pillar page
                                                                                                                                                                                - - Internal link from pillar page to every supporting page
                                                                                                                                                                                  - - Use descriptive anchor text that includes target keywords
                                                                                                                                                                                    - - Breadcrumb navigation on every subpage (with BreadcrumbList schema)
                                                                                                                                                                                     
                                                                                                                                                                                      - ---
                                                                                                                                                                                      
                                                                                                                                                                                      ## SECTION 5: PERFORMANCE & UX REQUIREMENTS
                                                                                                                                                                                      
                                                                                                                                                                                      ### 5.1 — Mobile-First Design (Non-Negotiable)
                                                                                                                                                                                      - All layouts MUST be responsive — mobile-first CSS approach
                                                                                                                                                                                      - - Touch targets minimum 44x44px
                                                                                                                                                                                        - - No horizontal scrolling on any viewport
                                                                                                                                                                                          - - Text readable without zooming (min 16px body font)
                                                                                                                                                                                            - - Test at: 320px, 375px, 768px, 1024px, 1280px, 1440px
                                                                                                                                                                                             
                                                                                                                                                                                              - ### 5.2 — Accessibility (WCAG 2.1 AA Minimum)
                                                                                                                                                                                              - - Color contrast ratio: minimum 4.5:1 for normal text, 3:1 for large text
                                                                                                                                                                                                - - All interactive elements keyboard-navigable
                                                                                                                                                                                                  - - ARIA labels on icon-only buttons
                                                                                                                                                                                                    - - Skip-to-content link as first focusable element
                                                                                                                                                                                                      - - Form fields have associated label elements
                                                                                                                                                                                                        - - Focus states visible on all interactive elements
                                                                                                                                                                                                         
                                                                                                                                                                                                          - ### 5.3 — Page Speed Optimization
                                                                                                                                                                                                          - - Total page weight: aim for under 500KB initial load
                                                                                                                                                                                                            - - JavaScript bundle: minimize, code-split per route
                                                                                                                                                                                                              - - Use dynamic imports for below-fold components
                                                                                                                                                                                                                - - Implement proper caching headers
                                                                                                                                                                                                                  - - Use CDN for static assets
                                                                                                                                                                                                                   
                                                                                                                                                                                                                    - ### 5.4 — Navigation & Internal Linking
                                                                                                                                                                                                                    - - Clear primary navigation with descriptive labels
                                                                                                                                                                                                                      - - Footer navigation with links to all major pages
                                                                                                                                                                                                                        - - Breadcrumbs on all pages beyond the homepage
                                                                                                                                                                                                                          - - Maximum 3 clicks to reach any page on the site
                                                                                                                                                                                                                            - - 404 page with helpful navigation back to key pages
                                                                                                                                                                                                                             
                                                                                                                                                                                                                              - ---
                                                                                                                                                                                                                              
                                                                                                                                                                                                                              ## SECTION 6: PRE-LAUNCH CHECKLIST
                                                                                                                                                                                                                              
                                                                                                                                                                                                                              Before declaring ANY website complete, verify ALL of the following:
                                                                                                                                                                                                                              
                                                                                                                                                                                                                              ### Technical SEO
                                                                                                                                                                                                                              - Every page has unique title and meta description
                                                                                                                                                                                                                              - - Only ONE h1 per page with primary keyword
                                                                                                                                                                                                                                - - Semantic HTML used throughout (no div-soup)
                                                                                                                                                                                                                                  - - All images have descriptive alt tags
                                                                                                                                                                                                                                    - - sitemap.xml generated and accessible
                                                                                                                                                                                                                                      - - robots.txt generated with AI crawlers allowed
                                                                                                                                                                                                                                        - - Canonical URLs set on every page
                                                                                                                                                                                                                                          - - Open Graph and Twitter Card meta on every page
                                                                                                                                                                                                                                            - - Clean URL structure (lowercase, hyphenated)
                                                                                                                                                                                                                                              - - Internal linking structure complete
                                                                                                                                                                                                                                                - - 404 page exists
                                                                                                                                                                                                                                                 
                                                                                                                                                                                                                                                  - ### Structured Data
                                                                                                                                                                                                                                                  - - Organization schema on every page
                                                                                                                                                                                                                                                    - - WebSite schema on homepage
                                                                                                                                                                                                                                                      - - FAQPage schema on FAQ sections
                                                                                                                                                                                                                                                        - - BreadcrumbList schema where breadcrumbs exist
                                                                                                                                                                                                                                                          - - Additional schemas for relevant content types
                                                                                                                                                                                                                                                            - - All JSON-LD validates at schema.org validator
                                                                                                                                                                                                                                                             
                                                                                                                                                                                                                                                              - ### Performance
                                                                                                                                                                                                                                                              - - All images use Next.js Image with proper sizing
                                                                                                                                                                                                                                                                - - Fonts loaded via next/font (no layout shift)
                                                                                                                                                                                                                                                                  - - Lazy loading on below-fold content
                                                                                                                                                                                                                                                                    - - No render-blocking CSS or JS
                                                                                                                                                                                                                                                                      - - Lighthouse Performance score: 90+
                                                                                                                                                                                                                                                                        - - Lighthouse SEO score: 95+
                                                                                                                                                                                                                                                                          - - Lighthouse Accessibility score: 90+
                                                                                                                                                                                                                                                                           
                                                                                                                                                                                                                                                                            - ### Content & GEO
                                                                                                                                                                                                                                                                            - - FAQ section with 5+ questions (visible + schema)
                                                                                                                                                                                                                                                                              - - Clear, definitive opening statements on every page
                                                                                                                                                                                                                                                                                - - E-E-A-T signals present (about page, credentials, trust indicators)
                                                                                                                                                                                                                                                                                  - - Privacy policy and terms of service pages exist
                                                                                                                                                                                                                                                                                    - - Contact information in footer
                                                                                                                                                                                                                                                                                      - - Quotable, cite-worthy statements throughout content
                                                                                                                                                                                                                                                                                       
                                                                                                                                                                                                                                                                                        - ### UX/UI
                                                                                                                                                                                                                                                                                        - Mobile responsive at all breakpoints
                                                                                                                                                                                                                                                                                        - - Touch targets 44x44px minimum
                                                                                                                                                                                                                                                                                          - - Keyboard navigation works throughout
                                                                                                                                                                                                                                                                                          - Color contrast meets WCAG 2.1 AA
                                                                                                                                                                                                                                                                                          - - Skip-to-content link present
                                                                                                                                                                                                                                                                                          - Smooth animations that do not block content rendering
                                                                                                                                                                                                                                                                                         
                                                                                                                                                                                                                                                                                          - ---
                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                          ## ENFORCEMENT RULE
                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                          When the user says the site is "done" or asks to "finalize" or "ship" the website:
                                                                                                                                                                                                                                                                                          1. Run through the ENTIRE pre-launch checklist above
                                                                                                                                                                                                                                                                                          2. 2. Report any missing items
                                                                                                                                                                                                                                                                                             3. 3. Fix all missing items automatically
                                                                                                                                                                                                                                                                                                4. 4. Only THEN confirm the site is ready to publish
                                                                                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                                                   5. NEVER mark a website as complete if ANY checklist item is missing.
