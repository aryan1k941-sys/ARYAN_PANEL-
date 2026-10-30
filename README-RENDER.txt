ARYAN PANEL STORE — RENDER DEPLOYMENT
=====================================

FILES
- index.html: customer website
- admin.html: admin dashboard
- render.yaml: Render Static Site configuration

DEPLOY ON RENDER (Android/mobile)
1. Extract this ZIP.
2. Upload the extracted files to a NEW GitHub repository (keep index.html, admin.html and render.yaml in the repository root).
3. Open https://render.com/ and sign in with GitHub.
4. New + -> Static Site -> connect the repository.
5. Render detects render.yaml. If entering settings manually: Build Command leave blank; Publish Directory = .
6. Deploy. Customer site: https://YOUR-SERVICE.onrender.com/
   Admin page: https://YOUR-SERVICE.onrender.com/admin (or /admin.html)

IMPORTANT FIREBASE SETUP
Both HTML files now point to the same Firebase project configuration that was already in index.html (xit-macro-vip). Render only hosts the HTML; Firebase still provides login/database.

A. Firebase Console: https://console.firebase.google.com/ -> project xit-macro-vip.
B. Authentication -> Sign-in method -> enable Email/Password.
C. Authentication -> Users: create/ensure the admin user email xitmacro007@gmail.com exists. The admin page allowlist only permits that email. Set its password yourself in Firebase; no password is included in this ZIP.
D. Realtime Database: ensure the database URL in index.html is active and that your database contains the expected paths: users, panels, payments, purchases, promotions, coupons, settings/payment, settings/branding, support_links.
E. Authentication -> Settings -> Authorized domains: add YOUR-SERVICE.onrender.com after first deploy.

SECURITY WARNING — READ BEFORE TAKING PAYMENTS
The supplied original app performs balance changes, coupon checks, key generation and purchases directly in browser JavaScript. This is NOT secure for a real-money store: a user can manipulate browser code or call Firebase directly unless strict Realtime Database rules and trusted server-side payment/purchase functions are implemented. Do not add real funds or accept real payments until the database rules and server-side verification are configured and tested. Never publish a payment gateway secret/API secret in HTML.

Firebase client apiKey is a public client identifier, not an admin password. Security must come from Firebase Authentication and Realtime Database Security Rules. Configure rules so users can only read/write their own permitted data and only the admin/server can approve payments, change balances, edit panels/settings, or issue keys.

NOT INCLUDED / NOT VERIFIED
- No FamGateway or other automatic payment gateway exists in the two uploaded HTML files; the current add-funds flow submits UTR details for manual admin approval.
- The project needs the Firebase account/database and admin account described above; deploying static HTML alone cannot create these.
- Verify the actual Firebase Realtime Database rules before production use.


NO START COMMAND
----------------
This is a Render Static Site. It does not require Python, Node, requirements.txt, or a start command. See DEPLOY-ON-ANDROID.txt.
