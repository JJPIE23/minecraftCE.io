# MinecraftCE

Static, browser-based voxel game. The root `index.html` and the `res/`, `steve/`, and `mobile_res/` folders are published directly with GitHub Pages.

GitHub Actions deploys the site whenever changes are pushed to `main`. Once the first deployment finishes, the site is available at:

https://jjpie23.github.io/minecraftCE.io/

Online multiplayer requires the site to be served over HTTPS.

On mobile, tap the game to request fullscreen and return to fullscreen when the tab becomes active. For browsers that do not allow fullscreen from a tab, add the site to the Home Screen and launch the installed app.

## Account sync setup

The Profile Settings page supports Google and email/password sign-in. Worlds, settings, profile data, and custom skins are synchronized to the signed-in Firebase account. Firebase modules load only when Profile Settings is opened.

Before using account sync in a Firebase project:

1. Enable Google and Email/Password under **Authentication → Sign-in method**.
2. Add `localhost` for local testing and `jjpie23.github.io` for the published site under **Authentication → Settings → Authorized domains**. Firebase sign-in does not work from a `file://` URL; from the repository root, run `python -m http.server 8000` and open `http://localhost:8000` when testing locally.
3. Create a Cloud Firestore database.
4. Sign in with the Firebase CLI (`firebase login`) and deploy the included owner-only rules from this repository: `firebase deploy --only firestore:rules --project chatapp-kids`.

The browser app uses the Firebase web configuration in `index.html`. Web API keys identify the Firebase project; Firestore access is restricted by `firestore.rules` to each authenticated user's own documents. Firebase Console provider and domain settings must be configured by a project administrator.
