# DHARA — Premium Redesign

## Deploy to GitHub Pages
Upload the **contents** of this folder to the repository `dharacollectiveorigin/dharacollectiveorigin.github.io` (not the ZIP).
In GitHub Settings → Pages, select Deploy from branch → main → /(root).

## Firebase
`firebase-config.js` contains public Firebase web-app identifiers for project `dhara-clothing`.
Before launch, set your admin UID in `firestore.rules` and publish the rules in Firebase Console.
Enable Email/Password and Anonymous Authentication. Add `dharacollectiveorigin.github.io` to authorized domains.
Admin dashboard: `/admin.html`. Set WhatsApp number in `contact-config.js`.

## Important
The initial concept products and stock are placeholders. Upload real products with your own product photos in Admin.
This site uses external editorial photographs from Unsplash for the hero/feature sections; replace with licensed brand photography for launch.
The bag is a preview: no real checkout, payments or order processing. WhatsApp is a direct link only; no two-way WhatsApp-to-site reply sync.
Customer chat uses anonymous Firebase authentication and Firestore; verify rules and test both customer/admin accounts before public launch.

Responsive design: `style.css` and `admin-responsive.css` are included. Upload both with the HTML and JS files.
