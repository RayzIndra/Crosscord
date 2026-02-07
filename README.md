# Site Discord Server - Guide de déploiement

## 🚀 Déploiement sur GitHub Pages

### Étape 1 : Créer un repository GitHub

1. Va sur [GitHub](https://github.com)
2. Clique sur "New repository"
3. Nomme-le par exemple : `discord-server-site`
4. Choisis "Public"
5. Crée le repository

### Étape 2 : Upload les fichiers

Deux méthodes possibles :

**Méthode 1 : Via l'interface web (facile)**
1. Clique sur "Add file" → "Upload files"
2. Glisse-dépose le fichier `index.html`
3. Commit les changements

**Méthode 2 : Via Git (recommandé)**
```bash
git clone https://github.com/TON-USERNAME/discord-server-site.git
cd discord-server-site
# Copie le fichier index.html dans ce dossier
git add index.html
git commit -m "Initial commit - Discord server website"
git push
```

### Étape 3 : Activer GitHub Pages

1. Va dans les Settings de ton repository
2. Scroll jusqu'à "Pages" dans le menu de gauche
3. Sous "Source", sélectionne "main" branch
4. Clique sur "Save"
5. Ton site sera disponible à : `https://TON-USERNAME.github.io/discord-server-site/`

## 🌐 Ajouter un nom de domaine personnalisé

### Option 1 : Domaine .org payant (10-15€/an)

1. **Achète un domaine .org** chez :
   - [Namecheap](https://namecheap.com) - ~10€/an
   - [OVH](https://ovh.com) - ~12€/an
   - [Google Domains](https://domains.google) - ~12€/an

2. **Configure le DNS** :
   - Ajoute un enregistrement `A` pointant vers :
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - Ou un enregistrement `CNAME` :
     ```
     TON-USERNAME.github.io
     ```

3. **Sur GitHub Pages** :
   - Va dans Settings → Pages
   - Entre ton nom de domaine dans "Custom domain"
   - Coche "Enforce HTTPS"

### Option 2 : Alternatives gratuites

**Freenom** (domaines .tk, .ml, .ga, .cf, .gq - GRATUITS)
- ⚠️ Attention : parfois instables, pas idéal pour du long terme
- Site : [freenom.com](https://freenom.com)

**Subdomaines gratuits** :
- `tonsite.is-a.dev` via [is-a-dev](https://is-a-dev.com)
- `tonsite.vercel.app` via Vercel
- Reste sur `tonsite.github.io` (100% fiable et gratuit)

## ✨ Fonctionnalités du site

### 1. **Section Partenariats**
- Système de vérification avec Rayz
- Formulaire de demande de partenariat
- Cartes interactives pour présenter les partenaires

### 2. **LLaMaHUB Integration**
- Section dédiée aux fonctionnalités IA
- Propulsé par Rayz
- 6 features principales présentées

### 3. **Blog**
- 3 articles de démonstration
- Design moderne avec cartes interactives
- Prêt pour ajouter de nouveaux articles

### 4. **Design**
- Style Discord moderne et minimaliste
- Animations fluides
- Responsive (mobile-friendly)
- Typographie unique (Syne + DM Sans)
- Palette de couleurs Discord officielle

## 🛠️ Personnalisation

### Modifier les couleurs
Édite les variables CSS dans `index.html` (lignes 11-21) :
```css
:root {
    --discord-blurple: #5865F2;
    --accent-green: #57F287;
    /* ... */
}
```

### Ajouter un article de blog
Duplique une carte blog dans la section `#blog` :
```html
<div class="blog-card">
    <div class="blog-image">🎯</div>
    <div class="blog-content">
        <div class="blog-meta">
            <span>7 février 2026</span>
            <span>•</span>
            <span>Catégorie</span>
        </div>
        <h3>Titre de l'article</h3>
        <p>Description...</p>
        <a href="#" class="read-more">Lire la suite →</a>
    </div>
</div>
```

### Modifier les stats
Change les chiffres dans la section `#hero` (lignes ~450-465).

### Connecter le formulaire de partenariat
Le formulaire actuel log les données dans la console. Pour le connecter :

**Option A : Discord Webhook**
```javascript
// Remplace la fonction submit (ligne ~730) par :
fetch('TON_WEBHOOK_URL', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
        embeds: [{
            title: "Nouvelle demande de partenariat",
            fields: [
                { name: "Serveur", value: formData.serverName },
                { name: "Membres", value: formData.serverMembers },
                { name: "Contact", value: formData.contact }
            ],
            color: 5814015
        }]
    })
});
```

**Option B : Google Forms / Typeform**
Remplace le formulaire par un iframe de Google Forms.

**Option C : Service backend (FormSpree, Basin.io)**
Gratuit pour ~50 soumissions/mois.

## 📱 Fonctionnalités additionnelles

### Ajouter un bouton Discord
```html
<a href="https://discord.gg/TON_INVITE" class="btn btn-primary">
    Rejoindre le Discord
</a>
```

### Widget Discord
Ajoute le widget dans la sidebar :
```html
<iframe src="https://discord.com/widget?id=TON_SERVER_ID&theme=dark" 
        width="350" height="500" frameborder="0"></iframe>
```

### Google Analytics (optionnel)
Ajoute avant `</head>` :
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

## 🔒 Sécurité & Bonnes pratiques

- ✅ HTTPS automatique avec GitHub Pages
- ✅ Pas de données sensibles dans le code
- ✅ Formulaires validés côté client
- ⚠️ Pour production : ajoute validation backend
- ⚠️ Protège tes webhooks Discord (ne les expose jamais publiquement)

## 📞 Support

Pour toute question :
- Ouvre une issue sur GitHub
- Contacte l'équipe via Discord
- Consulte la [documentation GitHub Pages](https://docs.github.com/pages)

## 📄 Licence

Site créé pour [Nom de ton serveur Discord]
Propulsé par Rayz - LLaMaHUB Integration

---

**Note importante sur les domaines .org gratuits** : Ils n'existent pas vraiment de manière fiable. Les seules options 100% gratuites et stables sont :
- `tonsite.github.io` ✅ Recommandé
- Subdomaines gratuits (`.is-a.dev`, etc.)

Pour un domaine .org professionnel, budget ~10-15€/an.
