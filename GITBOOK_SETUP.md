# GitBook Setup Guide

This guide will help you set up GitBook to host your StreamCraft Studios Custom HTML Library documentation.

## Option 1: GitBook.com (Recommended)

### 1. Create GitBook Account
- Go to [gitbook.com](https://gitbook.com)
- Sign up for a free account
- Create a new space

### 2. Connect Your GitHub Repository
- In your GitBook space, go to **Settings** → **Integrations**
- Connect your GitHub account
- Select the `custom-html-library` repository
- Choose the `main` branch

### 3. Configure Your Book
- GitBook will automatically detect your `book.json` and `SUMMARY.md`
- Your documentation will be available at `your-space.gitbook.io`

### 4. Custom Domain (Optional)
- Go to **Settings** → **Domains**
- Add your custom domain if desired

## Option 2: Self-Hosted GitBook

### 1. Install GitBook CLI
```bash
npm install -g gitbook-cli
```

### 2. Initialize Your Book
```bash
cd custom-html-library
gitbook init
```

### 3. Install Dependencies
```bash
gitbook install
```

### 4. Build and Serve
```bash
# Build the book
gitbook build

# Serve locally for development
gitbook serve
```

### 5. Deploy to GitHub Pages
```bash
# Build the book
gitbook build

# The built files will be in _book/ directory
# You can deploy this to GitHub Pages
```

## File Structure

Your GitBook structure should look like this:

```
custom-html-library/
├── book.json              # GitBook configuration
├── SUMMARY.md             # Table of contents
├── README.md              # Introduction page
├── docs/                  # Documentation files
│   ├── getting-started.md
│   ├── api-reference.md
│   ├── examples.md
│   └── best-practices.md
└── iframe-client.js       # Your library file
```

## Customization

### Themes
GitBook supports custom themes. You can modify the appearance by:
- Editing `book.json` plugins
- Adding custom CSS
- Using different theme plugins

### Plugins
The current configuration includes:
- **search**: Full-text search functionality
- **highlight**: Code syntax highlighting
- **github**: GitHub integration
- **expandable-chapters**: Collapsible navigation
- **copy-code-button**: Copy code to clipboard

## Publishing Updates

### With GitBook.com
- Push changes to your GitHub repository
- GitBook automatically syncs and updates

### With Self-Hosted
- Make changes to your markdown files
- Run `gitbook build` to rebuild
- Deploy the `_book/` directory

## Benefits of GitBook

✅ **Simple Markdown** - Write in easy-to-read markdown  
✅ **Automatic Navigation** - Table of contents from SUMMARY.md  
✅ **Search Functionality** - Full-text search across all content  
✅ **Responsive Design** - Works on all devices  
✅ **Version Control** - Integrates with Git  
✅ **Free Hosting** - GitBook.com provides free hosting  
✅ **Custom Domains** - Use your own domain if desired  

## Support

- [GitBook Documentation](https://docs.gitbook.com/)
- [GitBook Community](https://community.gitbook.com/)
- [Markdown Guide](https://www.markdownguide.org/)

---

Your documentation will be much easier to maintain and update with GitBook compared to the complex HTML approach!
