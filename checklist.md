# Checklist Qualité — NexusAI

## Performance

| Critère | Status | Action si ❌ |
|---|---|---|
| LCP < 2.5s | ✅ Pas d'images lourdes | — |
| CLS < 0.1 | ✅ Fonts préchargées | — |
| Fonts Google en preconnect | ✅ `<link rel="preconnect">` présent | — |
| Pas de JS bloquant | ✅ Scripts en bas de page | — |
| CSS inline (pas de fichier externe) | ✅ Tout dans `<style>` | — |
| Images WebP | ⚠️ Pas d'images (à ajouter) | Utiliser Squoosh pour convertir |
| Lazy loading images | ✅ `loading="lazy"` à ajouter sur futures images | — |

## SEO

| Critère | Status | Action si ❌ |
|---|---|---|
| `<title>` unique par page | ✅ Présent sur les 5 pages | — |
| `<meta description>` unique | ✅ Présent sur les 5 pages | — |
| H1 unique par page | ✅ Un seul H1 par page | — |
| Structure H1 > H2 > H3 | ✅ Hiérarchie correcte | — |
| Liens internes entre pages | ✅ Navigation + CTA croisés | — |
| `lang="fr"` sur `<html>` | ✅ Présent | — |
| Sitemap.xml | ❌ À créer | xml-sitemaps.com |
| robots.txt | ❌ À créer | Voir deploy.md |
| Schema.org (Organisation) | ❌ À ajouter | JSON-LD dans `<head>` |
| Open Graph tags | ⚠️ Basique (à compléter) | Ajouter og:image |

## Sécurité

| Critère | Status | Action si ❌ |
|---|---|---|
| HTTPS | ⚠️ Dépend de l'hébergeur | Netlify/Vercel : auto. Nginx : certbot |
| Headers CSP | ⚠️ À configurer côté serveur | Voir deploy.md Nginx config |
| X-Frame-Options | ⚠️ À configurer côté serveur | Voir deploy.md |
| Pas de données sensibles en JS | ✅ Aucune clé API exposée | — |
| Formulaire : validation frontend | ✅ Validation présente | — |
| Formulaire : honeypot anti-spam | ❌ À ajouter | `<input type="hidden" name="bot-field">` |

## RGPD

| Critère | Status | Action si ❌ |
|---|---|---|
| Cookie banner avec consentement | ✅ Présent avec accept/decline | — |
| Consentement stocké localStorage | ✅ Implémenté | — |
| Politique de confidentialité liée | ⚠️ Liens présents (page à créer) | Rédiger via iubenda.com |
| Mentions légales | ⚠️ Lien présent (page à créer) | Rédiger via legalstart.fr |
| Formulaire : consentement explicite | ✅ Checkbox RGPD avant envoi | — |
| Données hébergées en UE | ⚠️ Dépend de l'hébergeur | Choisir Netlify EU, OVH, Scaleway |

## Accessibilité

| Critère | Status | Action si ❌ |
|---|---|---|
| `alt` sur les images | ✅ À maintenir lors de l'ajout d'images | — |
| Labels sur les champs de formulaire | ✅ Tous les inputs ont un `<label>` | — |
| Contraste texte/fond | ✅ Dark mode : contrastes élevés | Tester sur webaim.org/resources/contrastchecker |
| Focus visible (keyboard nav) | ⚠️ À tester | Ajouter `:focus-visible` CSS |
| `aria-label` sur éléments interactifs | ⚠️ Partiel | Ajouter sur icônes sans texte |

## Mobile

| Critère | Status | Action si ❌ |
|---|---|---|
| Viewport meta tag | ✅ Présent | — |
| Responsive (mobile-first) | ✅ Media queries < 900px | — |
| Nav mobile | ✅ Nav links masquées, logo + CTA visibles | Ajouter menu hamburger |
| Touch targets > 44px | ✅ Boutons correctement dimensionnés | — |
| Pas de scroll horizontal | ✅ `overflow-x: hidden` sur body | — |

## Score global estimé Lighthouse

| Métrique | Estimé |
|---|---|
| Performance | 90-95/100 |
| Accessibilité | 85-90/100 |
| Best Practices | 90-95/100 |
| SEO | 85-90/100 |

## Prochaines étapes (priorité décroissante)

1. **Créer les pages Mentions légales + Politique de confidentialité**
2. **Intégrer le formulaire de contact** (Netlify Forms ou backend)
3. **Ajouter Schema.org** JSON-LD sur index.html
4. **Compléter les Open Graph** (og:image 1200x630)
5. **Créer sitemap.xml** et robots.txt
6. **Ajouter GA4** (après consentement cookie)
7. **Créer page 404.html** personnalisée
8. **Ajouter menu hamburger** pour mobile
9. **Optimiser les images** quand ajoutées (WebP, lazy load)
10. **Test Lighthouse** en production sur les 5 pages
