# Portfolio Website Deployment Guide

## Quick Setup: GitHub Pages + Custom Domain

### Prerequisites
- GitHub account
- Domain registrar account (Namecheap, etc.)
- Basic git knowledge

---

## Step 1: Prepare Website Files

```bash
# Ensure main HTML file is named index.html
mv code.html index.html

# Create required directories
mkdir -p images resume

# Add your images and resume PDF
```

---

## Step 2: Push to GitHub

```bash
# Initialize git (if not already done)
git init
git remote add origin git@github.com:username/repo-name.git

# Add files and commit
git add index.html images/ resume/
git commit -m "Initial portfolio deployment"

# Push to GitHub
git push origin main
```

---

## Step 3: Enable GitHub Pages

1. Go to repository settings: `github.com/username/repo-name/settings/pages`
2. Under "Source", select **main** branch
3. Click **Save**
4. Site will be live at: `https://username.github.io/repo-name/`

---

## Step 4: Purchase Domain

1. Go to domain registrar (e.g., Namecheap)
2. Search and purchase your domain (e.g., `yourname.net`)
3. Enable WHOIS privacy protection

---

## Step 5: Configure DNS

In your domain's DNS settings, add these records:

### A Records (for apex domain)
```
Type: A    Host: @    Value: 185.199.108.153
Type: A    Host: @    Value: 185.199.109.153
Type: A    Host: @    Value: 185.199.110.153
Type: A    Host: @    Value: 185.199.111.153
```

### CNAME Record (for www subdomain)
```
Type: CNAME    Host: www    Value: username.github.io
```

**Nameserver:** Use your registrar's default nameservers (e.g., Namecheap BasicDNS)

---

## Step 6: Add Custom Domain to GitHub Pages

1. Go to: `github.com/username/repo-name/settings/pages`
2. Under "Custom domain", enter: `yourname.net`
3. Click **Save**
4. Wait 15 minutes to 24 hours for DNS propagation
5. Once available, check **Enforce HTTPS**

---

## Verification

Test your website at:
- `http://yourname.net` (initially)
- `https://yourname.net` (after HTTPS is enabled)
- `https://www.yourname.net`

---

## Timeline

- DNS propagation: 15 minutes - 24 hours (usually < 1 hour)
- HTTPS certificate: 15 minutes - 24 hours
- Total deployment: ~30 minutes to 48 hours

---

## Cost

- **GitHub Pages:** FREE
- **Domain:** ~$10-15/year
- **Total:** ~$12/year

---

## Troubleshooting

### DNS not propagating
- Wait longer (up to 24 hours)
- Check DNS records are correct
- Use `dig yourname.net` to verify DNS

### HTTPS unavailable
- Wait for certificate to be issued
- Try removing and re-adding custom domain
- Ensure DNS is properly configured

### 404 Error
- Ensure `index.html` exists in root directory
- Check GitHub Pages is enabled on correct branch
- Verify repository is public

---

## Updating Your Website

```bash
# Make changes to files
git add .
git commit -m "Update portfolio"
git push origin main

# GitHub Pages auto-deploys in ~1 minute
```

---

## Project Structure

```
portfolio/
├── index.html          # Main website file
├── images/             # All images
│   ├── profile.jpg
│   ├── priya-photo.jpg
│   └── project-*.jpg
└── resume/             # Resume files
    └── Resume.pdf
```

---

## Resources

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Custom Domain Setup](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [Namecheap DNS Guide](https://www.namecheap.com/support/knowledgebase/article.aspx/319/2237/how-can-i-set-up-an-a-address-record-for-my-domain/)
