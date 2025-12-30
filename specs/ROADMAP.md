# umwai.github.io - Personal Site Roadmap

**Version**: 1.0
**Last Updated**: December 2025
**Site**: [umwai.github.io](https://umwai.github.io)

---

## Vision

A minimalist, high-performance personal portfolio site that showcases agentic engineering philosophy and professional experience. The site should serve as a digital business card, thought leadership platform, and project showcase.

---

## Current State (v1.0)

### What Exists
- Single-page static HTML site
- Dark theme with particle animation background
- Responsive design (mobile-friendly)
- Sections: Header, Philosophy, Background, Experience, Focus, Stack, Projects, Connect
- Animated favicon (SVG)
- No external dependencies or build system

### Performance Baseline
- Lighthouse Score: ~95+ (estimated)
- Load time: < 1s
- Zero JavaScript dependencies
- < 20KB total page size

---

## Roadmap Phases

| Phase | Timeline | Focus | Effort |
|-------|----------|-------|--------|
| **Phase 1: Content Enhancement** | Q1 2026 | Writing & thought leadership | Low |
| **Phase 2: Technical Polish** | Q2 2026 | Performance & SEO | Low |
| **Phase 3: Interactive Features** | Q3 2026 | Blog & engagement | Medium |
| **Phase 4: Personal Brand** | Q4 2026 | Speaking & visibility | Medium |

---

## Phase 1: Content Enhancement (Q1 2026)

### Objective
Establish thought leadership in agentic engineering

### Deliverables

#### 1.1 Blog Section
- [ ] Add `/blog` or `/writing` section
- [ ] 3-5 cornerstone articles on agentic engineering
- [ ] RSS feed for subscribers

**Proposed Articles**:
1. "Context Engineering: The 80/20 of AI Development"
2. "Multi-Agent Orchestration Patterns for Production"
3. "From Vibe Coding to Agentic Engineering: A Mindset Shift"
4. "Building Self-Healing Data Pipelines with Claude"
5. "The Core 4: Context, Model, Prompt, Tools"

#### 1.2 Case Studies
- [ ] Add detailed project case studies
- [ ] Include: Problem, Approach, Results, Learnings
- [ ] Projects to feature:
  - Sonata AI chatbot (Claude + FastAPI)
  - RNA-seq pipeline automation
  - Databricks Lakehouse implementation

#### 1.3 Speaking & Media
- [ ] Add speaking section (if applicable)
- [ ] Conference talks or podcast appearances
- [ ] Embed video content (if available)

### Success Metrics
- [ ] 5+ articles published
- [ ] 3+ case studies complete
- [ ] Organic traffic from Google (measurable)

---

## Phase 2: Technical Polish (Q2 2026)

### Objective
Optimize performance, SEO, and accessibility

### Deliverables

#### 2.1 SEO Optimization
- [ ] Meta tags optimization
- [ ] Open Graph images (custom og-image.png)
- [ ] Structured data (JSON-LD for Person)
- [ ] Sitemap.xml
- [ ] robots.txt

**Structured Data Example**:
```json
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Wai Yang",
  "jobTitle": "Senior Data Engineer",
  "worksFor": {
    "@type": "Organization",
    "name": "Paratus Sciences"
  },
  "url": "https://umwai.github.io",
  "sameAs": [
    "https://github.com/UMwai",
    "https://linkedin.com/in/..."
  ]
}
```

#### 2.2 Performance Optimization
- [ ] Image optimization (WebP, lazy loading)
- [ ] Critical CSS inlining (already done)
- [ ] Preconnect hints for external resources
- [ ] Service worker for offline support (optional)

#### 2.3 Accessibility
- [ ] ARIA labels for interactive elements
- [ ] Keyboard navigation support
- [ ] Color contrast verification
- [ ] Screen reader testing

#### 2.4 Analytics
- [ ] Privacy-respecting analytics (Plausible or Fathom)
- [ ] Event tracking (project clicks, contact clicks)
- [ ] Monthly traffic dashboard

### Success Metrics
- [ ] Lighthouse score: 100 across all categories
- [ ] Core Web Vitals: All green
- [ ] WCAG 2.1 AA compliance

---

## Phase 3: Interactive Features (Q3 2026)

### Objective
Increase engagement and provide value to visitors

### Deliverables

#### 3.1 Interactive Elements
- [ ] Terminal-style command interface (easter egg)
- [ ] Project hover previews with screenshots
- [ ] Animated timeline interactions
- [ ] Dark/light mode toggle (optional)

**Terminal Easter Egg Concept**:
```
Press Ctrl+` to open terminal
> help
Available commands: about, projects, contact, resume
> projects
Loading projects...
```

#### 3.2 Contact Improvements
- [ ] Contact form (Formspree or similar)
- [ ] Calendar booking link (Calendly)
- [ ] Response time expectation

#### 3.3 Newsletter/Updates
- [ ] Email signup for blog updates
- [ ] Integration with ConvertKit/Buttondown
- [ ] Welcome automation sequence

### Success Metrics
- [ ] 50+ newsletter subscribers
- [ ] 10+ contact form submissions/month
- [ ] Average session duration > 2 minutes

---

## Phase 4: Personal Brand (Q4 2026)

### Objective
Establish presence in agentic engineering community

### Deliverables

#### 4.1 Community Engagement
- [ ] Twitter/X presence linked from site
- [ ] GitHub contribution showcase
- [ ] Open source project highlights

#### 4.2 Speaking & Visibility
- [ ] Conference talk proposals
- [ ] Podcast guest appearances
- [ ] YouTube channel (optional)

#### 4.3 Networking
- [ ] "Work with me" section
- [ ] Consulting/advisory offerings
- [ ] Testimonials section

### Success Metrics
- [ ] 1+ conference talk given
- [ ] 2+ podcast appearances
- [ ] Inbound opportunities from site

---

## Content Calendar

### Q1 2026
| Month | Content | Type |
|-------|---------|------|
| Jan | "Context Engineering: The 80/20" | Blog |
| Feb | Sonata AI Chatbot Case Study | Case Study |
| Mar | "Multi-Agent Orchestration Patterns" | Blog |

### Q2 2026
| Month | Content | Type |
|-------|---------|------|
| Apr | RNA-seq Pipeline Case Study | Case Study |
| May | "From Vibe Coding to Agentic Engineering" | Blog |
| Jun | Technical SEO implementation | Technical |

### Q3 2026
| Month | Content | Type |
|-------|---------|------|
| Jul | Terminal easter egg | Feature |
| Aug | Newsletter launch | Feature |
| Sep | "The Core 4" article | Blog |

### Q4 2026
| Month | Content | Type |
|-------|---------|------|
| Oct | Speaking/podcast push | Visibility |
| Nov | "Work with me" section | Feature |
| Dec | Year in review post | Blog |

---

## Technical Decisions

### Build System
**Decision**: Stay with no-build static HTML
**Rationale**:
- Maximum simplicity and performance
- No dependencies to maintain
- GitHub Pages native deployment
- Easy to understand and modify

**Alternative Considered**: Astro/11ty
- Would add complexity for minimal benefit
- Current site is already optimal
- Revisit if blog grows significantly

### Blog Implementation Options

| Option | Pros | Cons |
|--------|------|------|
| **Same HTML page** | Simple, no new pages | Gets unwieldy |
| **Separate HTML files** | Simple, SEO-friendly | Manual management |
| **Astro** | Markdown support, fast | Build step required |
| **Ghost** | Full CMS | External hosting |

**Recommendation**: Start with separate HTML files, migrate to Astro if > 10 posts

### Analytics
**Recommendation**: Plausible Analytics
- Privacy-respecting (GDPR compliant)
- Simple dashboard
- $9/mo or self-hosted
- No cookie banner needed

---

## Design Evolution

### Current Design Language
- Monospace typography (SF Mono, Fira Code)
- Dark theme (#0a0a0a background)
- Blue accent (#4a9eff)
- Subtle animations (particles, fade-in)
- Minimal chrome, content-focused

### Future Enhancements
- Subtle gradient backgrounds (optional)
- Code syntax highlighting for blog
- Project screenshots/thumbnails
- Micro-interactions on hover states

### Design Principles (Maintain)
1. **Performance first** - No heavy frameworks
2. **Content is king** - Design serves content
3. **Subtle animation** - Enhance, don't distract
4. **Mobile-native** - Works perfectly on phones
5. **Dark by default** - Matches developer aesthetic

---

## Maintenance Schedule

| Task | Frequency | Notes |
|------|-----------|-------|
| Update experience section | As needed | Job changes |
| Update projects | Quarterly | New repos |
| Check broken links | Monthly | Use link checker |
| Review analytics | Weekly | Traffic patterns |
| Update dependencies | N/A | No dependencies |
| SSL certificate | Automatic | GitHub Pages |

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | Dec 2025 | Initial site launch |
| 1.1 | TBD | SEO optimization |
| 2.0 | TBD | Blog section added |

---

*This roadmap is reviewed quarterly and adjusted based on priorities and opportunities.*
