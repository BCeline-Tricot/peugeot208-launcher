# Launcher Peugeot 208 (autoradio Android)

Launcher **natif** (Kotlin + OpenGL ES 2.0, sans WebView) avec une Peugeot 208 en 3D.
Cible : autoradio Android 15, MT8163, 2 Go de RAM, écran 1280x720.

## Obtenir l'APK avec GitHub (sans Android Studio)
1. Crée un dépôt GitHub (vide), puis envoie-y **tout le contenu de ce dossier** (bouton *Add file > Upload files*,
   y compris le dossier `.github`, qui est caché : glisse-le à part si besoin).
2. Onglet **Actions** : le workflow *Build APK* démarre tout seul (sinon *Run workflow*). Compte 3 à 6 minutes.
3. Ouvre l'exécution terminée, section **Artifacts** : télécharge `peugeot208-launcher-apk` (un zip contenant `app-debug.apk`).

## Installer sur l'autoradio
1. Copie `app-debug.apk` sur une clé USB, ouvre-la avec le gestionnaire de fichiers de l'autoradio, autorise les sources inconnues, installe.
2. Appuie sur la touche Home : Android propose de choisir le launcher, prends **Peugeot 208** (« Toujours »).
3. Pour revenir à l'ancien : Paramètres > Applications > Applications par défaut > Appli d'accueil.

## À adapter : `app/src/main/java/com/peugeot208/launcher/Config.kt`
- `RADIO` : paquet de l'appli Radio de ton autoradio (vide = message d'aide).
- `NAV`, `MUSIC`, `BLUETOOTH`, `BOTTOM` : les applis lancées par le menu et la barre du bas.
- `VehicleState` : valeurs de démonstration (carburant, vitesse, température) à brancher sur le CAN.

## Voiture 3D
`tools/make_car_bin.py` convertit un GLB en `app/src/main/assets/car.bin` :
`python3 tools/make_car_bin.py tools/car_painted.glb app/src/main/assets/car.bin`
