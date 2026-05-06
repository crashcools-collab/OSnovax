# NexusAI — Structure du site

## Arborescence

```
nexus-site/
├── index.html          → Accueil (Hero, Services, Process, Portfolio, Témoignages, Blog preview, CTA)
├── services.html       → Services détaillés + Pricing + FAQ
├── portfolio.html      → Cas clients filtrables + Métriques
├── blog.html           → Articles + Sidebar + Newsletter
├── contact.html        → Formulaire de contact qualifié
├── structure.md        → Ce fichier
├── deploy.md           → Instructions de déploiement
└── checklist.md        → Audit qualité
```

## Pages & Sections

### index.html — Accueil
| Section | Contenu |
|---|---|
| Nav | Logo, liens, CTA "Démarrer un projet" |
| Hero | Badge statut + H1 animé + sous-titre + CTA + Stats (47 projets, 3.2M€, 98%) |
| Services | 6 cartes (Agents IA, Automatisation, Fine-tuning, Data pipelines, API, Audit) |
| Process | 4 étapes (Audit J1-3, Architecture J4-7, Dev J8-25, Deploy J26-30) + Terminal animé |
| Portfolio | 3 cas clients (Finance, Santé, Retail) |
| Témoignages | 3 cartes (SaaS, Santé, Retail) |
| Blog | 3 articles récents |
| CTA | Capture email + bouton |
| Footer | 4 colonnes + RGPD + Cookie banner |

### services.html — Services
| Section | Contenu |
|---|---|
| Page Hero | Breadcrumb + H1 + description |
| Services détaillés | 3 services expandés (Agents, Automatisation, Fine-tuning) avec cas d'usage + métriques |
| Pricing | 3 plans (Starter 2500€, Growth 7500€, Enterprise sur devis) |
| FAQ | 6 questions/réponses |

### portfolio.html — Portfolio
| Section | Contenu |
|---|---|
| Stats bande | 5 métriques globales |
| Filtres | Finance, Santé, Retail, SaaS, Logistique |
| Cases | 6 études de cas avec métriques réelles |
| CTA | Lien vers contact |

### blog.html — Blog
| Section | Contenu |
|---|---|
| Hero + Newsletter | Titre + formulaire d'abonnement inline |
| Tags | 8 catégories filtrables |
| Layout 2 colonnes | 1 article featured + 7 articles liste / Sidebar sticky |
| Sidebar | Top 4 articles + Tag cloud + Widget CTA |

### contact.html — Contact
| Section | Contenu |
|---|---|
| Layout split 50/50 | Left: infos + trust / Right: formulaire |
| Formulaire | Prénom, Nom, Email, Tel, Entreprise, Secteur, Type projet, Budget, Urgence, Message |
| RGPD | Consentement explicite avant envoi |
| Success state | Animation confirmation post-envoi |

## Palette & Design System

```css
--bg: #050508        /* Background principal */
--bg2: #0c0c14       /* Background secondaire */
--accent: #4F46E5    /* Violet principal */
--green: #10B981     /* Vert accent */
--white: #F0EEF8     /* Texte principal */
--muted: #6b6b8a     /* Texte secondaire */
--border: rgba(79,70,229,0.18) /* Bordures */
```

## Typographie
- **Display** : Syne (400, 700, 800) — Google Fonts
- **Mono** : DM Mono (300, 400) — Google Fonts

## Composants réutilisables
- `.btn-primary` — CTA violet avec hover glow
- `.btn-ghost` — Bouton outline avec hover
- `.section-label` — Label vert mono uppercase
- `.hero-grid-bg` — Grille CSS en arrière-plan
- `.terminal` — Widget terminal animé
- Cookie banner avec localStorage

## Logique UX
```
Visiteur → Hero (Hook) → Services (Proposition) → Portfolio (Preuve) → CTA (Conversion)
Visiteur → Blog (SEO) → Sidebar CTA → Contact
```
