# MATEC Wallet — Guide Build iOS (Capacitor)

## Prérequis
- Mac avec macOS 13 (Ventura) ou supérieur
- Xcode 15+ (téléchargeable depuis le Mac App Store)
- Compte Apple Developer (99 USD/an) — https://developer.apple.com
- Node.js 18+ et npm 9+

## Étapes rapides (5 commandes)

```bash
# 1. Se placer dans ce dossier
cd matec_capacitor_ios/

# 2. Installer les dépendances Capacitor
npm install

# 3. Ajouter la plateforme iOS
npx cap add ios

# 4. Synchroniser
npx cap sync ios

# 5. Ouvrir dans Xcode
npx cap open ios
```

## Dans Xcode

1. Dans Xcode → TARGETS → App → Signing & Capabilities
2. Choisir votre **Team** (votre compte Apple Developer)
3. **Bundle Identifier** : `site.matec.app`
4. Product → Archive → Distribute App → App Store Connect

## Permissions à ajouter dans Info.plist (Xcode)
```xml
<key>NSCameraUsageDescription</key>
<string>MATEC Wallet utilise la caméra pour scanner les QR codes.</string>
<key>NSPhotoLibraryUsageDescription</key>
<string>Accès aux photos pour envoyer des justificatifs de paiement.</string>
<key>NSFaceIDUsageDescription</key>
<string>Authentification biométrique pour sécuriser votre wallet.</string>
```

## App Transport Security (iOS)
Vérifier que le domaine matec.site est autorisé dans Info.plist :
```xml
<key>NSAppTransportSecurity</key>
<dict>
    <key>NSAllowsArbitraryLoads</key>
    <false/>
    <key>NSExceptionDomains</key>
    <dict>
        <key>matec.site</key>
        <dict>
            <key>NSExceptionAllowsInsecureHTTPLoads</key>
            <false/>
            <key>NSIncludesSubdomains</key>
            <true/>
        </dict>
    </dict>
</dict>
```

## Icônes iOS requises
Les icônes se trouvent dans `../ios_icons/` :
- 20x20, 29x29, 40x40, 60x60, 76x76, 83.5x83.5 (iPad)
- 1024x1024 (App Store)
Copier dans Xcode → App → Assets.xcassets → AppIcon

## URL de démarrage
https://matec.site/my/matec-wallet
