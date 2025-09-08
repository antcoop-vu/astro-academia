# Astro Academia

Astro Academia is a personal academic website template built using Astro 5, React, TailwindCSS, and DaisyUI. The website showcases academic achievements, research areas, publications, CV, and blog posts. It is fast, responsive, and designed for academics and researchers.

Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.

## Working Effectively

### Bootstrap, build, and test the repository:
- Install Node.js v22.11.0 (specified in .nvmrc): `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash && export NVM_DIR="$HOME/.nvm" && [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" && nvm install && nvm use` -- takes ~30 seconds. NEVER CANCEL. Set timeout to 300+ seconds.
- Install dependencies: `npm install` -- takes ~6-25 seconds. NEVER CANCEL. Set timeout to 120+ seconds.
- Build the project: `npm run build` -- takes ~4-6 seconds. NEVER CANCEL. Set timeout to 60+ seconds.

### Run the application:
- ALWAYS run the bootstrapping steps first (Node.js install, npm install).
- Development server: `npm run dev` -- starts in ~1 second, serves at http://localhost:4321/astro-academia
- Preview production build: `npm run preview` -- starts in ~1 second, serves at http://localhost:4321/astro-academia
- Available commands: `npm run` to see all available scripts

### Validation
- ALWAYS manually validate any changes by running the development server and testing functionality.
- Key validation scenarios to test after making changes:
  - Homepage loads with profile, research areas, and recent publications
  - Blog listing page (/blog/1) displays all blog posts correctly
  - Individual blog posts render markdown content including tables and formatting
  - CV page displays education, experience, publications, and skills from cv.ts data
  - Navigation between all pages (Home, Research, Papers, CV, Blog) works correctly
  - Social media links and footer elements display properly
- ALWAYS test responsive design by resizing browser window.
- MANDATORY: After adding new blog posts, verify they appear in the blog listing and are accessible via direct URL.
- MANDATORY: After modifying settings.ts or cv.ts, verify changes appear correctly on relevant pages.
- There are NO linting, formatting, or testing scripts configured in this project.
- The CI/CD pipeline (.github/workflows/deploy.yml) only builds and deploys - no additional validation steps required.

### Manual Testing Checklist
Run through this checklist after making any changes:
1. Start dev server: `npm run dev`
2. Visit http://localhost:4321/astro-academia and verify homepage loads
3. Click through all navigation links (Home, Research, Papers, CV, Blog)
4. On blog page, click individual post links to verify they render correctly
5. Verify any changes you made appear as expected
6. Test responsive behavior by resizing browser window

## Project Structure and Key Files

### Critical Configuration Files:
- `src/settings.ts` -- MOST IMPORTANT: Contains all site configuration including profile info, social links, theme settings, and website URL
- `src/data/cv.ts` -- Contains CV data (education, experience, publications, skills)
- `astro.config.mjs` -- Astro configuration with integrations and site settings
- `package.json` -- Dependencies and npm scripts
- `.nvmrc` -- Node.js version specification (v22.11.0)

### Content Management:
- `src/content/BlogPosts/` -- Contains markdown blog posts with frontmatter (title, date, excerpt, tags)
- `src/content.config.ts` -- Defines content collection schema for blog posts
- `src/assets/` -- Static assets including profile pictures and images

### Component Structure:
- `src/layouts/Layout.astro` -- Main layout wrapper
- `src/components/ui/` -- Reusable UI components (Navbar, Footer, etc.)
- `src/pages/` -- Astro pages (index.astro, cv.astro, research.astro, etc.)

### Build Output:
- `dist/` -- Generated static site files (created by `npm run build`)

## Common Development Tasks

### Adding a New Blog Post:
1. Create new markdown file in `src/content/BlogPosts/` (e.g., `new-post.md`)
2. Add frontmatter with required fields:
   ```markdown
   ---
   title: "Post Title"
   date: "2025-01-01"
   excerpt: "Brief description"
   tags: ["tag1", "tag2"]
   ---
   ```
3. Write content in markdown format
4. Test by running `npm run dev` and navigating to /blog/1

### Updating Site Configuration:
- Edit `src/settings.ts` to change:
  - Profile information (name, title, institute)
  - Social media links
  - Theme settings (lightTheme, darkTheme)
  - Website URL and base path
  - Menu preferences

### Updating CV Content:
- Edit `src/data/cv.ts` to modify:
  - Education history
  - Work experience
  - Publications list
  - Skills and competencies

### Customizing Styling:
- Global styles: `tailwind.config.mjs` for Tailwind configuration
- Theme customization: DaisyUI themes in `src/settings.ts`
- Component-specific styling: Edit individual .astro files

## Deployment Information

### GitHub Pages Deployment:
- Automatic deployment via `.github/workflows/deploy.yml`
- Triggers on push to `main` branch
- Uses `withastro/action@v3` for build and deployment
- Deploys to GitHub Pages at configured URL in `src/settings.ts`

### Local Preview:
- Build production version: `npm run build`
- Preview locally: `npm run preview`
- Development with hot reload: `npm run dev`

## Technology Stack Details

### Core Technologies:
- **Astro 5.1.6** -- Static site generator with component islands
- **React 19.0.0** -- UI library for interactive components
- **TailwindCSS 3.4.17** -- Utility-first CSS framework
- **DaisyUI 4.12.23** -- Component library for Tailwind

### Key Dependencies:
- `@astrojs/react` -- React integration for Astro
- `@astrojs/sitemap` -- Automatic sitemap generation
- `@astrojs/rss` -- RSS feed generation
- `theme-change` -- Dark/light theme switching

## Troubleshooting

### Common Issues:
- **Build fails**: Ensure Node.js v22.11.0 is installed (check with `node --version`)
- **Development server won't start**: Run `npm install` to ensure dependencies are installed
- **Images not loading**: Check file paths in `src/assets/` and verify imports
- **Styling issues**: Verify DaisyUI theme names in `src/settings.ts` match available themes
- **Content not updating**: Restart dev server after adding new blog posts or changing content configuration
- **Port already in use**: Kill existing processes on port 4321 or use different port with `npm run dev -- --port 3000`
- **Build warnings about browserslist**: Safe to ignore, or update with `npx update-browserslist-db@latest`

### Performance Notes:
- Build process is very fast (~5 seconds) due to Astro's static generation
- No bundle size concerns as output is static HTML/CSS/JS
- Images are automatically optimized during build process

## Common command reference

### Repository root structure:
```
.
├── .github/workflows/deploy.yml
├── .nvmrc (v22.11.0)
├── README.md
├── astro.config.mjs
├── package.json
├── src/
│   ├── assets/
│   ├── components/
│   ├── content/
│   ├── data/
│   ├── layouts/
│   ├── pages/
│   └── settings.ts
├── tailwind.config.mjs
└── tsconfig.json
```

### Key npm scripts:
- `npm run dev` -- Start development server
- `npm run build` -- Build for production
- `npm run preview` -- Preview production build
- `npm run astro` -- Run Astro CLI commands

Always validate changes by running the development server and testing all key functionality before committing changes.