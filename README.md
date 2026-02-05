# 🚀 b3prompt.com - AI Prompt Improvement Course

Master AI prompting with our comprehensive course. Learn vibe coding, prompt templates, and advanced techniques.

## 🌟 Featured Lesson

### 🎨 Universal Vibe Coding Prompt Lesson
**NEW & SHINING!**

Learn to create stunning multi-page websites using AI!

- 📝 Universal prompt template (copy & paste ready)
- 🎯 Real-world case study (Sunset Portfolio)
- ✨ Design elements that boost engagement
- 📱 Mobile testing checklist
- 🔍 SEO optimization guide
- 🚀 Deployment to Cloudflare Pages, Netlify, Vercel, GitHub Pages

**Read the lesson:** [`content/universal-vibe-coding-lesson.html`](content/universal-vibe-coding-lesson.html)

## ☁️ Auto-Deploy to Cloudflare Pages

This site auto-deploys from GitHub to Cloudflare Pages!

### Setup Cloudflare Pages (One-Time)

1. **Create Cloudflare Pages project:**
   - Go to: https://dash.cloudflare.com/?to=/:pages/new
   - Connect to GitHub
   - Select: `ib3rt/b3prompt`
   - Framework preset: **None** (static site)
   - Build command: (leave empty)
   - Output directory: (leave empty)

2. **Add custom domain:**
   - Settings → Custom domains
   - Add: `b3prompt.com`
   - Point DNS to Cloudflare

### GitHub Actions (Auto-Deploy)

The `.github/workflows/deploy.yml` file handles auto-deployment:
- Push to `master` → Auto-deploy to Cloudflare Pages
- Custom domain `b3prompt.com` configured
- Instant global CDN

## 📚 Course Content

### Core Modules
1. Prompt Basics
2. Structure & Format
3. Specificity
4. Refinement
5. Advanced Tactics
6. Applications

### Special Lessons
- **🎨 Universal Vibe Coding** (NEW!)
  - Complete prompt template for website creation
  - Real implementation (Sunset Portfolio)
  - Deployment guide for multiple platforms

## 📁 Project Structure

```
b3prompt/
├── index.html                    # Landing page (redesigned to feature new lesson!)
├── content/
│   ├── universal-vibe-coding-lesson.md    # Original markdown lesson
│   └── universal-vibe-coding-lesson.html  # HTML version (NEW!)
├── course/
│   └── index.md                  # Course overview
├── cloudflare-pages.toml         # Cloudflare Pages config
├── .github/workflows/
│   └── deploy.yml                # Auto-deploy workflow
└── README.md                     # This file
```

## 🛠️ Development

### Local Development
```bash
# Clone repo
git clone https://github.com/ib3rt/b3prompt.git
cd b3prompt

# Preview locally
python3 -m http.server 8000
# Open http://localhost:8000
```

### Add New Content
1. Create content in `content/` folder (markdown or HTML)
2. Update `index.html` to feature it
3. Push to GitHub
4. Auto-deploys via Cloudflare Pages

### Deploy Process
```
GitHub Push → GitHub Actions → Cloudflare Pages → Live! ⚡
```

## 🎯 Features

- ✅ Featured lesson prominently displayed
- ✅ Complete course modules
- ✅ Prompt templates library
- ✅ Practice exercises
- ✅ Quick tips section
- ✅ Responsive design
- ✅ Dark mode support
- ✅ SEO optimized
- ✅ Auto-deploy to Cloudflare Pages
- ✅ Custom domain: b3prompt.com

## 🔗 Links

- **Live Site:** https://b3prompt.com (after Cloudflare setup)
- **Repository:** https://github.com/ib3rt/b3prompt
- **Sunset Portfolio Example:** https://github.com/ib3rt/sunset-portfolio

## 📝 License

Open source - feel free to use and adapt!

---

*Master AI prompting. Create amazing things.* ✨
