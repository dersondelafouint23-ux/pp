# ROMANTIK PWA 💕

**La plateforme de l'amour** - Application Web Progressive

## 📋 Description

Ce projet est une PWA (Progressive Web App) qui encapsule votre application web hébergée sur `http://localhost:3000` dans une interface native, prête à être convertie en APK via PWABuilder.

## 🎯 Caractéristiques

- ✅ Manifest PWA complet (`manifest.json`)
- ✅ Service Worker pour fonctionnement offline
- ✅ WebView intégré pointant vers `http://localhost:3000`
- ✅ Icônes personnalisées (logo ROMANTIK)
- ✅ Thème blanc élégant
- ✅ Écran de chargement avec animation
- ✅ Compatible PWABuilder pour génération APK

## 📁 Structure du projet

```
romantik-pwa/
├── index.html              # Page principale avec WebView
├── manifest.json           # Manifest PWA (app.json)
├── service-worker.js       # Service Worker pour cache et offline
├── icons/
│   ├── icon-192x192.png   # Icône 192x192
│   └── icon-512x512.png   # Icône 512x512 (logo ROMANTIK)
└── README.md              # Ce fichier
```

## 🚀 Déploiement sur Cloudflare Pages

### Option 1: Via Cloudflare Dashboard

1. Connectez-vous à [dash.cloudflare.com](https://dash.cloudflare.com)
2. Allez dans **Pages** > **Create a project**
3. Choisissez **Upload assets**
4. Glissez-déposez tous les fichiers de ce projet
5. Cliquez sur **Deploy site**
6. Notez l'URL fournie (ex: `https://romantik.pages.dev`)

### Option 2: Via Wrangler CLI

```bash
# Installer Wrangler
npm install -g wrangler

# Se connecter à Cloudflare
wrangler login

# Déployer le projet
wrangler pages publish romantik-pwa --project-name=romantik
```

## 📱 Générer l'APK avec PWABuilder

### Étape 1: Héberger sur Cloudflare
Déployez d'abord votre projet sur Cloudflare Pages (voir ci-dessus)

### Étape 2: Utiliser PWABuilder

1. Allez sur [https://www.pwabuilder.com](https://www.pwabuilder.com)
2. Entrez l'URL de votre site Cloudflare (ex: `https://romantik.pages.dev`)
3. Cliquez sur **Start** pour analyser votre PWA
4. Vérifiez le score et les recommandations
5. Cliquez sur **Package For Stores**
6. Sélectionnez **Android** 
7. Configurez les options:
   - **Package ID**: `com.romantik.app` (ou votre préférence)
   - **App name**: ROMANTIK
   - **Version**: 1.0.0
8. Téléchargez le package APK ou AAB
9. Votre APK est prêt pour tests ou publication sur Google Play Store!

## ⚙️ Configuration importante

### Modifier l'URL de destination

Pour changer l'URL vers laquelle pointe la WebView, éditez:

**Dans `manifest.json`:**
```json
"start_url": "http://localhost:3000"
```

**Dans `index.html`:**
```html
<iframe src="http://localhost:3000" ...>
```

### Changer les couleurs

**Dans `manifest.json`:**
```json
"theme_color": "#FFFFFF",
"background_color": "#FFFFFF"
```

## 🔧 Test en local

1. Installez un serveur HTTP local:
```bash
npm install -g http-server
```

2. Lancez le serveur:
```bash
cd romantik-pwa
http-server -p 8080
```

3. Ouvrez votre navigateur sur `http://localhost:8080`

## 📱 Test PWA

### Chrome/Edge Desktop
1. Ouvrez votre site
2. Cliquez sur l'icône d'installation dans la barre d'adresse
3. Testez l'application installée

### Chrome Mobile
1. Ouvrez votre site sur mobile
2. Menu > **Ajouter à l'écran d'accueil**
3. Testez comme une app native

## 🎨 Personnalisation des icônes

Les icônes actuelles utilisent le logo ROMANTIK. Pour les modifier:

1. Remplacez les fichiers dans `/icons/`
2. Générez différentes tailles (192x192, 512x512)
3. Outil recommandé: [PWA Image Generator](https://www.pwabuilder.com/imageGenerator)

## 📦 Fichiers générés pour PWABuilder

- ✅ `manifest.json` - Conforme aux spécifications PWA
- ✅ `service-worker.js` - Cache et fonctionnement offline
- ✅ Icônes multiples tailles
- ✅ HTML responsive et compatible mobile

## 🔗 Ressources utiles

- [PWABuilder Documentation](https://docs.pwabuilder.com/)
- [Cloudflare Pages Docs](https://developers.cloudflare.com/pages/)
- [Web.dev - PWA Guide](https://web.dev/progressive-web-apps/)

## 📝 Notes importantes

1. **Pour la production**: Changez `http://localhost:3000` par l'URL réelle de votre application
2. **HTTPS requis**: PWABuilder nécessite HTTPS (Cloudflare le fournit automatiquement)
3. **Service Worker**: Fonctionne uniquement en HTTPS (sauf localhost)
4. **Test local**: Utilisez `http-server` ou tout serveur web local

## 🆘 Support

En cas de problème avec PWABuilder:
- Documentation: [docs.pwabuilder.com](https://docs.pwabuilder.com/)
- GitHub: [github.com/pwa-builder](https://github.com/pwa-builder)

---

**Développé pour ROMANTIK - La plateforme de l'amour** 💕
