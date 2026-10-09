# Binéro — fabriquer l'APK

## Méthode A (recommandée) : GitHub fabrique l'APK pour toi
Aucun logiciel à installer. Il faut un compte GitHub gratuit.

1. Va sur github.com, crée un compte (ou connecte-toi).
2. Clique sur « + » en haut à droite > « New repository ». Nom : binero. Laisse « Public » ou « Private », puis « Create repository ».
3. Sur la page du dépôt, clique « uploading an existing file ».
4. Dézippe cette archive sur ton ordinateur, puis glisse TOUT le contenu du dossier (dont le dossier caché .github) dans la fenêtre. Attention : il faut envoyer les fichiers, pas le .zip.
   Si .github n'est pas pris par le glisser-déposer : utilise « Add file > Create new file » et tape le nom `.github/workflows/build-apk.yml`, puis colle le contenu du fichier.
5. Clique « Commit changes ».
6. Onglet « Actions » : le workflow « Construire l'APK » se lance tout seul (sinon : clique dessus puis « Run workflow »). Compte 5 à 10 minutes.
7. Quand la pastille est verte, clique sur l'exécution, descends jusqu'à « Artifacts » et télécharge « binero-apk ». Dézippe : tu obtiens app-debug.apk.

## Installer l'APK sur Android
1. Envoie app-debug.apk sur le téléphone (câble USB, mail, WhatsApp, Drive).
2. Ouvre-le. Android demande d'autoriser l'installation depuis cette source : accepte (Paramètres > Installer des applis inconnues).
3. Si Play Protect avertit, choisis « Installer quand même ».

## Méthode B : sur ton ordinateur (Android Studio)
1. Installe Node.js 20, Java 17 et Android Studio.
2. Dans ce dossier : `npm install`, puis `npx cap add android`, puis `npx cap sync android`.
3. `npx cap open android` ouvre Android Studio. Menu Build > Build APK(s).
4. L'APK est dans android/app/build/outputs/apk/debug/.

## Modifier le jeu plus tard
Remplace www/index.html par la nouvelle version, renvoie-la sur GitHub (Add file > Upload files), et le robot refabrique l'APK.

## Publier sur le Play Store (optionnel)
L'APK « debug » sert à installer chez des proches. Pour le Play Store il faut un compte développeur (25 $ une fois), une clé de signature et un fichier AAB (`./gradlew bundleRelease`). Demande-moi si tu veux faire cette étape.
