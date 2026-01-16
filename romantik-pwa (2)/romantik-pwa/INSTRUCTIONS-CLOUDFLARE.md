# 🚀 Guide de Déploiement ROMANTIK sur Cloudflare Pages

## 📦 Contenu du projet

Votre projet **ROMANTIK PWA** est prêt avec :

- ✅ `app.json` / `manifest.json` - Configuration PWA
- ✅ `index.html` - Page principale avec WebView vers `http://localhost:3000`
- ✅ `service-worker.js` - Fonctionnement offline
- ✅ `icons/` - Logo ROMANTIK (192x192 et 512x512)
- ✅ Thème blanc personnalisé

## 🌐 Étape 1 : Déployer sur Cloudflare Pages

### Méthode A : Via l'interface web (RECOMMANDÉ)

1. **Connectez-vous à Cloudflare**
   - Allez sur [dash.cloudflare.com](https://dash.cloudflare.com)
   - Connectez-vous avec votre compte

2. **Créer un nouveau projet Pages**
   - Dans le menu latéral, cliquez sur **Pages**
   - Cliquez sur **Create a project**
   - Choisissez **Upload assets** (Direct Upload)

3. **Télécharger les fichiers**
   - Décompressez le fichier `romantik-pwa.zip`
   - Glissez-déposez TOUS les fichiers et dossiers dans Cloudflare
   - Ou cliquez sur **Select from computer** et choisissez les fichiers

4. **Nommer votre projet**
   - Nom du projet : `romantik` (ou ce que vous voulez)
   - Cliquez sur **Deploy site**

5. **Récupérer votre URL**
   - Une fois déployé, vous aurez une URL comme :
   - `https://romantik.pages.dev`
   - ⚠️ **Notez bien cette URL !** Vous en aurez besoin pour PWABuilder

### Méthode B : Via Wrangler CLI (Pour développeurs)

```bash
# Installer Wrangler
npm install -g wrangler

# Se connecter
wrangler login

# Déployer
cd romantik-pwa
wrangler pages deploy . --project-name=romantik
```

## 📱 Étape 2 : Générer l'APK avec PWABuilder

### 2.1 Accéder à PWABuilder

1. Ouvrez [https://www.pwabuilder.com](https://www.pwabuilder.com)
2. Dans le champ, entrez votre URL Cloudflare : `https://romantik.pages.dev`
3. Cliquez sur **Start**

### 2.2 Analyser votre PWA

- PWABuilder va analyser votre site
- Vous verrez un score PWA
- Vérifiez que tout est vert ✅

### 2.3 Générer le package Android

1. Cliquez sur **Package For Stores**
2. Sélectionnez **Android** (icône robot vert)
3. **Configurer les options** :

   ```
   Package ID: com.romantik.app
   App name: ROMANTIK
   App version: 1.0.0
   Version code: 1
   Host: romantik.pages.dev
   Signing key: Generate (pour la première fois)
   ```

4. **Options avancées** (optionnel) :
   - Display mode: `standalone`
   - Orientation: `portrait`
   - Background color: `#FFFFFF`
   - Theme color: `#FFFFFF`

5. Cliquez sur **Generate**

### 2.4 Télécharger l'APK

- Choisissez le format :
  - **APK** : Pour tests et distribution directe
  - **AAB** : Pour Google Play Store (recommandé)
  
- Téléchargez le fichier
- Conservez le **signing key** en lieu sûr !

## ⚙️ Étape 3 : Modifier l'URL de production

⚠️ **IMPORTANT** : Avant de publier sur le Play Store, changez l'URL !

### Option 1 : URL de votre vraie application

Si votre app est hébergée sur `https://mon-app.com` :

1. Éditez `manifest.json` / `app.json` :
```json
"start_url": "https://mon-app.com"
```

2. Éditez `index.html` :
```html
<iframe src="https://mon-app.com" ...>
```

3. Redéployez sur Cloudflare
4. Re-générez l'APK avec PWABuilder

### Option 2 : Garder localhost pour le développement

Si vous voulez que l'APK se connecte à votre serveur local :
- ✅ L'URL `http://localhost:3000` est déjà configurée
- ⚠️ Cela ne fonctionnera que sur les appareils où le serveur tourne
- Utilisé généralement pour le développement/tests

## 🧪 Étape 4 : Tester l'APK

### Sur Android

1. Transférez l'APK sur votre téléphone
2. Activez **Sources inconnues** dans les paramètres
3. Installez l'APK
4. Lancez l'application ROMANTIK

### Avec un émulateur

1. Ouvrez Android Studio
2. Lancez un émulateur Android
3. Glissez-déposez l'APK dans l'émulateur
4. Testez l'application

## 🏪 Étape 5 : Publier sur Google Play Store

### Prérequis

- Compte développeur Google Play (25$ unique)
- AAB signé (généré par PWABuilder)
- Icônes et screenshots
- Description de l'app

### Publication

1. Allez sur [play.google.com/console](https://play.google.com/console)
2. Créez une nouvelle application
3. Remplissez les informations :
   - Nom : ROMANTIK
   - Description : La plateforme de l'amour
   - Catégorie : Réseaux sociaux / Lifestyle
   - Icônes et screenshots
4. Téléchargez l'AAB dans **Production** > **Create release**
5. Soumettez pour révision

### Temps d'approbation
- Première soumission : 7-14 jours
- Mises à jour : 1-3 jours

## 🔄 Mise à jour de l'application

Pour mettre à jour votre app :

1. Modifiez vos fichiers localement
2. Redéployez sur Cloudflare Pages
3. Re-générez l'APK avec PWABuilder (version +1)
4. Publiez sur Play Store

## ⚠️ Points importants

- ✅ **HTTPS obligatoire** : PWA nécessite HTTPS (Cloudflare le fournit)
- ✅ **Service Worker** : Ne fonctionne qu'en HTTPS
- ✅ **Icônes** : Logo ROMANTIK déjà configuré
- ✅ **Thème** : Blanc comme demandé
- ⚠️ **localhost:3000** : Changez pour production !

## 🆘 Problèmes courants

### "PWA score trop faible"
- Vérifiez que manifest.json est accessible
- Vérifiez que service-worker.js fonctionne
- Testez sur HTTPS uniquement

### "Icons not found"
- Vérifiez que le dossier `icons/` est bien uploadé
- Les icônes doivent être en PNG
- Chemins relatifs : `icons/icon-512x512.png`

### "Service Worker not registered"
- Fonctionne uniquement en HTTPS
- Videz le cache du navigateur
- Vérifiez la console développeur

## 📞 Support

- **PWABuilder Docs** : [docs.pwabuilder.com](https://docs.pwabuilder.com/)
- **Cloudflare Docs** : [developers.cloudflare.com/pages](https://developers.cloudflare.com/pages/)
- **Google Play Console** : [support.google.com/googleplay](https://support.google.com/googleplay)

---

**Bon déploiement ! 🚀 ROMANTIK - La plateforme de l'amour** 💕
