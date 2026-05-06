# Deploy — NexusAI

## Option 1 : Netlify Drop (0 config, 2 minutes)

```bash
# Glisser-déposer le dossier nexus-site/ sur app.netlify.com/drop
# → URL publique immédiate (ex: https://nexusai.netlify.app)
# → Domaine custom : Netlify > Domain settings > Add domain
```

## Option 2 : GitHub + Netlify CI/CD

```bash
# 1. Push sur GitHub
git init
git add .
git commit -m "feat: initial NexusAI site"
git remote add origin https://github.com/VOTRE_USER/nexusai-site.git
git push -u origin main

# 2. Netlify : New site → Import from Git → Sélectionner le repo
# Build command : (vide, site statique)
# Publish directory : /
# → Déploiement auto à chaque git push
```

## Option 3 : Vercel CLI

```bash
npm i -g vercel
cd nexus-site/
vercel
# Suivre les prompts → URL de preview
vercel --prod
# → Production deployée
```

## Option 4 : GitHub Pages

```bash
# Repo Settings → Pages → Source: main branch → / (root)
# URL : https://VOTRE_USER.github.io/nexusai-site
```

## Option 5 : Serveur Apache/Nginx

```nginx
# /etc/nginx/sites-available/nexusai
server {
    listen 80;
    server_name nexusai.fr www.nexusai.fr;
    root /var/www/nexusai;
    index index.html;

    # Gzip
    gzip on;
    gzip_types text/html text/css application/javascript;

    # Cache headers
    location ~* \.(css|js|png|jpg|webp|svg|ico)$ {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }

    # Security headers
    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-Content-Type-Options "nosniff";
    add_header Referrer-Policy "strict-origin-when-cross-origin";
    add_header Content-Security-Policy "default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src https://fonts.gstatic.com;";

    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

```bash
# Déployer les fichiers
scp -r nexus-site/ user@your-server:/var/www/nexusai/
nginx -t && systemctl reload nginx
```

## Checklist pré-déploiement

- [ ] Remplacer `hello@nexusai.fr` par votre vrai email dans `contact.html`
- [ ] Remplacer `NexusAI` / `nexusai.fr` par votre nom de marque et domaine
- [ ] Tester le formulaire de contact (intégrer Netlify Forms, Formspree ou endpoint backend)
- [ ] Vérifier sur mobile (Chrome DevTools → toggle device)
- [ ] Ajouter Google Analytics : `<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX">` dans chaque `<head>`
- [ ] Générer et uploader `sitemap.xml` (outil : xml-sitemaps.com)
- [ ] Créer `robots.txt` à la racine
- [ ] Configurer domaine custom + HTTPS (Let's Encrypt / Netlify auto SSL)
- [ ] Tester Lighthouse sur les 5 pages (objectif > 90 partout)

## robots.txt (à créer)

```txt
User-agent: *
Allow: /

Sitemap: https://votre-domaine.fr/sitemap.xml
```

## Intégration formulaire de contact (Netlify Forms)

Ajouter `netlify` au tag `<form>` dans contact.html :
```html
<form name="contact" method="POST" netlify netlify-honeypot="bot-field">
  <input type="hidden" name="form-name" value="contact">
  <!-- champs existants -->
</form>
```
→ Réponses dans Netlify Dashboard > Forms
→ Notifications email configurables
