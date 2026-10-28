# DHARA — Wear Your Story

GitHub Pages static storefront with Firebase-backed product management and website messaging.

## Setup (required before features work)
1. Open `contact-config.js` and set your WhatsApp number in international digits (e.g. 8801XXXXXXXXX, without +). This enables the direct WhatsApp button inside website chat. The button opens WhatsApp; it does not sync messages back to the website.
9. Create a Firebase project and web app. Copy its web configuration into `firebase-config.js`.
9. Enable **Authentication** > Email/Password and Anonymous sign-in.
9. Create your own admin user using Firebase Authentication console (Email/Password). Copy the admin UID from Firebase Authentication > Users.
9. Replace `REPLACE_WITH_ADMIN_UID` in `firestore.rules` with the exact admin UID from Authentication > Users. Publish these rules in Firebase Firestore > Rules. **Do not publish the placeholder rules.**
9. Enable Cloud Firestore. If prompted for a collection-group index for `messages` ordered by `createdAt`, create it from the Firebase console link in the error.
9. Add `dharacollectiveorigin.github.io` to Firebase Authentication authorized domains.
9. Create a GitHub repository named `dharacollectiveorigin.github.io` under the matching GitHub username. Upload these files to the repository root and enable Pages from main/root.
9. Visit `/admin.html` and sign in. Add your products, images, prices, discounts, and stock. Customer messages appear in the inbox and replies appear on the website.

## Important limitations
- **WhatsApp two-way messaging is NOT implemented.** It requires approved WhatsApp Business Platform API, webhooks, server hosting, and compliance with Meta rules; GitHub Pages alone cannot do it.
- Store chat uses anonymous Firebase accounts; customers must return using the same browser/auth session to see replies. It is not a durable cross-device inbox.
- Add rate limiting, abuse controls/App Check, privacy notice, and retention policies before public launch.
- Image URLs must be HTTPS and trusted; use Firebase Storage or another image host. File uploads are not yet implemented.
- Checkout/payment and order management are not implemented.
- Sample products are placeholders until real Firestore products are added.
- Firebase config is public by design; protect access with Firestore rules, not by hiding config.

## Features
- Website live chat: customer sends a message, admin replies in `admin.html`, and reply appears in the customer’s website chat on the same anonymous browser session.
- WhatsApp direct chat: customer clicks the WhatsApp button and talks to your personal WhatsApp inside WhatsApp. Replies remain in WhatsApp.
- Do not put passwords, API keys, or WhatsApp access tokens in GitHub Pages source.
- **Not deployed**: you must configure Firebase and publish GitHub Pages using your accounts.


## Social media settings (new)
Admin Panel → Social media settings supports Facebook, Instagram, YouTube and TikTok links. Save updates to Firestore `settings/social`; the storefront footer reads these live. Blank links hide their labels. Copy the updated `firestore.rules` into Firebase Console → Firestore → Rules, replace `REPLACE_WITH_ADMIN_UID` with the admin Firebase Auth UID, and Publish before using this feature.

## GitHub upload
Unzip the archive and upload the **files inside** to the root of the repository (not the ZIP and not a containing folder). On an empty repository click **uploading an existing file**; on an existing repository click **Add file → Upload files**. Commit, then Settings → Pages → Deploy from a branch → main → /(root) → Save.
