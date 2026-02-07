# 🚀 Guide de Démarrage Rapide - ✟cord

## Site Discord Chrétien Professionnel Noir & Blanc

**Thème** : Design pro noir et blanc  
**Nom** : ✟cord  
**Focus** : Communauté chrétienne ouverte à tous  
**Partenariats** : Rayz + LAMAstream (https://rayzindra.github.io/LAMAstream/)

---

## Déployer en 5 minutes sur GitHub Pages

### 1️⃣ Préparation (2 min)

**Ce dont tu as besoin :**
- Un compte GitHub (gratuit sur github.com)
- Les fichiers du site (déjà prêts !)

**Fichiers inclus :**
```
├── index.html                    # Page principale (noir & blanc pro)
├── blog-article-template.html    # Template pour articles
├── robots.txt                    # Fichier pour Google (indexation)
├── sitemap.xml                   # Plan du site pour Google
├── SEO-GUIDE.md                  # Guide complet référencement Google
├── README.md                     # Documentation complète
├── _config.yml                   # Config GitHub Pages
└── QUICK-START.md               # Ce fichier
```

### 2️⃣ Upload sur GitHub (2 min)

**Option A : Via l'interface web (le plus simple)**

1. Va sur https://github.com/new
2. Nomme ton repo : `discord-server-site` (ou autre)
3. Clique "Create repository"
4. Clique "uploading an existing file"
5. Glisse tous les fichiers dans la zone
6. Clique "Commit changes"

**Option B : Via Git (si tu connais)**

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/TON-USERNAME/discord-server-site.git
git push -u origin main
```

### 3️⃣ Activer GitHub Pages (1 min)

1. Dans ton repo, clique sur **Settings** (⚙️)
2. Dans le menu de gauche, clique sur **Pages**
3. Sous "Source", sélectionne **main** branch
4. Clique **Save**
5. Attends 1-2 minutes ⏰

**🎉 Ton site sera accessible à :**
```
https://TON-USERNAME.github.io/discord-server-site/
```

---

## 🔍 Être Visible sur Google

### Étapes Essentielles (5 min)

**1. Upload les fichiers robots.txt et sitemap.xml**
- Ils sont déjà créés dans ton package
- Upload-les avec les autres fichiers sur GitHub

**2. Modifie sitemap.xml et robots.txt**
- Ouvre `sitemap.xml`
- Remplace `TON-USERNAME` par ton nom d'utilisateur GitHub
- Remplace `TON-REPO` par le nom de ton repository
- Fais pareil dans `robots.txt`

**3. Soumet ton site à Google (CRUCIAL)**

1. Va sur https://search.google.com/search-console
2. Ajoute ta propriété : `https://ton-username.github.io/ton-repo/`
3. Vérifie la propriété (télécharge fichier HTML ou utilise balise)
4. Une fois vérifié, va dans "Sitemaps"
5. Entre `sitemap.xml` et clique "Envoyer"

**Résultat** : Ton site apparaîtra sur Google en 24-48h !

📖 **Pour plus de détails** : Lis le fichier `SEO-GUIDE.md`

---

## 📝 Personnalisation Rapide

### Changer le nom du serveur

Ouvre `index.html` et cherche ligne ~15 :
```html
<div class="logo">Discord Server</div>
```
Remplace par :
```html
<div class="logo">Ton Serveur Discord</div>
```

### Modifier le titre de la page

Ligne ~6 :
```html
<title>Ton Serveur - Communauté & Partenariats</title>
```

### Ajouter le lien Discord

Cherche ligne ~443 :
```html
<a href="#" class="btn btn-primary">Rejoindre le Discord</a>
```
Remplace par :
```html
<a href="https://discord.gg/TON_CODE_INVITE" class="btn btn-primary">Rejoindre le Discord</a>
```

### Changer les statistiques

Lignes ~455-468, modifie les chiffres :
```html
<div class="stat-number">2.5K+</div>  <!-- Tes vrais chiffres -->
<div class="stat-label">Membres actifs</div>
```

---

## 🎨 Personnalisation Avancée

### Couleurs

Le site utilise un thème **noir et blanc professionnel**. 

Édite les variables CSS (lignes 19-28) si tu veux changer :
```css
:root {
    --primary: #000000;           /* Noir principal */
    --secondary: #1a1a1a;         /* Noir secondaire */
    --accent: #333333;            /* Gris accent */
    --text-primary: #FFFFFF;      /* Texte blanc */
    --text-secondary: #CCCCCC;    /* Texte gris clair */
    /* Modifie ces valeurs si nécessaire */
}
```

### Ajouter un article de blog

1. Duplique `blog-article-template.html`
2. Renomme-le : `article-nom-de-ton-article.html`
3. Édite le contenu
4. Dans `index.html`, ajoute le lien :
```html
<a href="article-nom-de-ton-article.html" class="read-more">Lire la suite →</a>
```

---

## 🔗 Connecter le formulaire

### Option 1 : Discord Webhook (Gratuit, Facile)

1. Dans ton serveur Discord : Paramètres → Intégrations → Webhooks
2. Crée un webhook, copie l'URL
3. Dans `index.html`, ligne ~730, remplace par :

```javascript
document.getElementById('partnershipForm').addEventListener('submit', async function(e) {
    e.preventDefault();
    
    const formData = {
        serverName: document.getElementById('serverName').value,
        serverMembers: document.getElementById('serverMembers').value,
        serverInvite: document.getElementById('serverInvite').value,
        description: document.getElementById('description').value,
        contact: document.getElementById('contact').value
    };

    // Envoie vers Discord
    await fetch('TON_WEBHOOK_URL_ICI', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
            embeds: [{
                title: "📝 Nouvelle demande de partenariat",
                fields: [
                    { name: "🏷️ Serveur", value: formData.serverName, inline: true },
                    { name: "👥 Membres", value: formData.serverMembers, inline: true },
                    { name: "🔗 Invitation", value: formData.serverInvite },
                    { name: "📧 Contact", value: formData.contact },
                    { name: "📄 Description", value: formData.description }
                ],
                color: 5814015,
                timestamp: new Date()
            }]
        })
    });

    alert('✅ Demande envoyée !');
    this.reset();
});
```

### Option 2 : Google Forms

1. Crée un Google Form
2. Récupère le lien d'iframe
3. Remplace la section formulaire par :
```html
<iframe src="TON_LIEN_GOOGLE_FORM" width="100%" height="800"></iframe>
```

---

## 🌐 Nom de Domaine Personnalisé

### Domaines GRATUITS (avec limitations)

**1. Rester sur GitHub**
- `tonsite.github.io` ← **RECOMMANDÉ**
- 100% fiable, SSL gratuit, rapide

**2. is-a.dev (gratuit)**
- Demande : https://is-a-dev.com
- Donne : `tonsite.is-a.dev`
- Processus : Pull Request sur GitHub

**3. Freenom (risqué)**
- Domaines : .tk, .ml, .ga, .cf, .gq
- ⚠️ Peuvent être révoqués sans préavis
- Site : freenom.com

### Domaines PAYANTS (recommandé pour sérieux)

**Domaine .org : ~10-15€/an**

1. **Achète le domaine** :
   - Namecheap : ~10€/an
   - OVH : ~12€/an
   - Google Domains : ~12€/an

2. **Configure le DNS** (chez ton registrar) :
   
   **Méthode A - Enregistrement A (plus stable)**
   ```
   Type: A
   Host: @
   Value: 185.199.108.153
   
   Type: A
   Host: @
   Value: 185.199.109.153
   
   Type: A
   Host: @
   Value: 185.199.110.153
   
   Type: A
   Host: @
   Value: 185.199.111.153
   ```

   **Méthode B - Enregistrement CNAME**
   ```
   Type: CNAME
   Host: www
   Value: TON-USERNAME.github.io
   ```

3. **Sur GitHub Pages** :
   - Settings → Pages
   - Custom domain : `tondomaine.org`
   - ✅ Enforce HTTPS

4. **Attends 24-48h** pour propagation DNS

---

## 🛠️ Fonctionnalités Supplémentaires

### Widget Discord embarqué

Ajoute dans `index.html` où tu veux :
```html
<iframe 
    src="https://discord.com/widget?id=TON_SERVER_ID&theme=dark" 
    width="350" 
    height="500" 
    allowtransparency="true" 
    frameborder="0" 
    sandbox="allow-popups allow-popups-to-escape-sandbox allow-same-origin allow-scripts">
</iframe>
```

Pour obtenir l'ID du serveur : Paramètres serveur → Widget

### Google Analytics

Avant `</head>` dans `index.html` :
```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### Favicon (icône du site)

1. Crée une image 512x512px
2. Convertis en .ico sur https://favicon.io
3. Upload `favicon.ico` dans ton repo
4. Ajoute dans `<head>` :
```html
<link rel="icon" type="image/x-icon" href="favicon.ico">
```

---

## ✅ Checklist de Lancement

Avant de partager ton site :

- [ ] Personnalisé le nom (✟cord est déjà défini)
- [ ] Ajouté le vrai lien d'invitation Discord
- [ ] Modifié les statistiques (1.8K+ membres, etc.)
- [ ] Mis à jour sitemap.xml avec tes vraies URLs
- [ ] Mis à jour robots.txt avec tes vraies URLs
- [ ] Uploadé robots.txt et sitemap.xml sur GitHub
- [ ] Testé le formulaire de partenariat
- [ ] Configuré Google Search Console
- [ ] Soumis le sitemap à Google
- [ ] Vérifié sur mobile (responsive ✅)
- [ ] Ajouté un favicon (optionnel)
- [ ] Configuré le domaine (si applicable)
- [ ] Testé tous les liens (LAMAstream, etc.)
- [ ] Relu le contenu (fautes de frappe)

---

## 🆘 Problèmes Courants

### Le site ne s'affiche pas après activation

- ⏰ Attends 2-5 minutes
- 🔄 Vide le cache : Ctrl+F5 (ou Cmd+Shift+R sur Mac)
- ✅ Vérifie que la branche est bien "main" dans Settings → Pages

### Le formulaire ne fonctionne pas

- 🔗 Vérifie que tu as bien remplacé `TON_WEBHOOK_URL`
- 🌐 Teste dans la console du navigateur (F12)
- 📝 Regarde les erreurs dans la console

### Les images de police ne chargent pas

- ✅ Vérifie ta connexion internet
- 🔗 Les polices Google Fonts nécessitent une connexion

### Le site est lent

- ⚡ Active "Enforce HTTPS" dans GitHub Pages
- 🌐 Utilise un CDN pour les images si tu en ajoutes

---

## 📚 Ressources Utiles

- [Documentation GitHub Pages](https://docs.github.com/pages)
- [Discord Developer Portal](https://discord.com/developers)
- [Google Fonts](https://fonts.google.com)
- [Can I Use](https://caniuse.com) - Compatibilité navigateurs

---

## 💬 Support

Besoin d'aide ?
- 📖 Lis le README.md complet
- 🔍 Google ton erreur
- 💬 Demande dans ton serveur Discord
- 🐛 Ouvre une issue sur GitHub

---

**Créé pour ✟cord - Communauté Chrétienne Discord**  
Propulsé par Rayz & LAMAstream  
Design professionnel noir & blanc
